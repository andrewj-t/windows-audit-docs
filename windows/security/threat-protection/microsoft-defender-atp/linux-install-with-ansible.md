---
title: Installing Microsoft Defender ATP for Linux with Puppet
ms.reviewer: 
description: Describes how to install Microsoft Defender ATP for Linux, using Puppet.
keywords: microsoft, defender, atp, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance 
ms.topic: conceptual
---

# Ansible based deployment

**Applies to:**

- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) for Linux](microsoft-defender-atp-linux.md)

This topic describes how to deploy Microsoft Defender ATP for Linux through Ansible. A successful deployment requires the completion of all of the following steps:

- [Download the onboarding packages](#download-onboarding-package)
- [Create Ansible YAML files](#create-ansible-yaml-files)
- [Deployment](#deployment)
- [References](#references)

## Prerequisites and system requirements

Before you get started, please see [the main Microsoft Defender ATP for Linux page](microsoft-defender-atp-linux.md) for a description of prerequisites and system requirements for the current software version.

- Ansible needs to be installed at least on one computer (we will call it master)
- Password less SSH must be configured for root user between Master and all clients
- Below software must be installed on all clients
  - python-apt
  - curl
  - unzip

- All host must be listed in the following format in `/etc/ansible/hosts` file
    
    ```bash
    [servers]
    host1 ansible_ssh_host=10.171.134.39
    host2 ansible_ssh_host=51.143.50.51
    ```

- Ping test

    ```$ ansible -m ping all```

## Download onboarding package

Download the onboarding package from Microsoft Defender Security Center:

1. In Microsoft Defender Security Center, go to **Settings > Machine Management > Onboarding**.
2. In the first drop down, set operating system to **Linux Server** and in second drop down, Deployment method to **Your preferred Linux configuration management tool**.
3. Click on **Download package**. Save it as WindowsDefenderATPOnboardingPackage.zip.

    ![Microsoft Defender Security Center screenshot](images/atp-portal-onboarding-linux-2.png)

4. From a command prompt, verify that you have the file. Extract the contents of the archive:
  
    ```bash
    $ ls -l
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    $ unzip WindowsDefenderATPOnboardingPackage.zip
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## Create Ansible YAML files

Create subtask / role files which contribute to an actual task. Create below files under `/etc/ansible/roles` directory.

- Copy onboarding package on all client machines  

    ```bash
    $ cat /etc/ansible/roles/copy_onboarding_pkg.yml
    - name: Copy the zip file
        copy:
            src:  /root/WindowsDefenderATPOnboardingPackage.zip
            dest: /root/WindowsDefenderATPOnboardingPackage.zip
            owner: root
            group: root
            mode: '0644'
    ```

- Create a `setup.sh` script which operates on the onboarding file

    ```bash
    $ cat /root/setup.sh

    #!/bin/bash

    # Unzip the file and create license file
    mkdir -p /etc/opt/microsoft/mdatp/
    unzip WindowsDefenderATPOnboardingPackage.zip
    cp mdatp_onboard.json /etc/opt/microsoft/mdatp/mdatp_onboard.json

    # get the GPG key
    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
    sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/
    ```

- Create onboarding blob

    ```bash
    $ cat setup_blob.yml
    - name: Copy the setup script file
        copy:
            src: /root/setup.sh
            dest: /root/setup.sh
            owner: root
            group: root
            mode: '0744'

    - name: Run a script to create license blob
        script: /root/setup.sh
    ```

- Add the Microsoft Defender ATP repository and key

    Microsoft Defender ATP for Linux can be deployed from one of the following channels (denoted below as *[channel]*): *insider-fast* or *prod*. Each of these channels corresponds to a Linux software repository.

    The choice of the channel determines the type and frequency of updates that are offered to your device. Devices in *insider-fast* can try out new features before devices in *prod*.

    In order to preview new features and provide early feedback, it is recommended that you configure some devices in your enterprise to use the *insider-fast* channel.

    Note your distribution and version and identify the closest entry for it under `https://packages.microsoft.com/config/`.

    In the below commands, replace *[distro]* and *[version]* with the information identified in the previous step.

    - For apt-based distributions use the following YAML file

        ```bash
        $ cat add_apt_repo.yml
        - name: Add Microsoft repository for MDATP
            apt_repository:
                repo: deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/[distro]/[version]/prod [channel] main
                update_cache: yes
                state: present
                filename: microsoft-[channel].list

        - name: Add Microsoft APT key
                apt_key:
                    keyserver: https://packages.microsoft.com/
                    id: BC528686B50D79E339D3721CEB3E94ADBE1229C
        ```

    - For yum-based distributions use the following YAML file

        ```bash
        $ cat add_yum_repo.yml
        - name: Add  Microsoft repository for MDATP
            yum_repository:
                name: packages-microsoft-com-prod-[channel]
                description: Microsoft Defender ATP
                file: microsoft-[channel]
                baseurl: https://packages.microsoft.com/[distro]/[version]/[channel]/
                gpgcheck: yes
                enabled: Yes
        ```

- Create the actual install / uninstall YAML files under `/etc/ansible/playbooks`

    - For apt-based distributions use the following YAML file

        ```bash
        $ cat install_mdatp.yml
        - hosts: servers
            tasks:
                - include: ../roles/download_copy_blob.yml
                - include: ../roles/setup_blob.yml
                - include: ../roles/add_apt_repo.yml
                - apt:
                    name: mdatp
                    state: latest
                    update_cache: yes
        ```

        ```bash
        $ cat uninstall_mdatp.yml
        - hosts: servers
        tasks:
            - apt:
                name: mdatp
                state: absent
        ```

    - For yum-based distributions use the following YAML file

        ```bash
        $ cat install_mdatp_yum.yml
        - hosts: servers
        tasks:
            - include: ../roles/download_copy_blob.yml
            - include: ../roles/setup_blob.yml
            - include: ../roles/add_yum_repo.yml
            - yum:
                name: mdatp
                state: latest
                enablerepo: packages-microsoft-com-prod-insiders-fast
        ```

        ```bash
        $ cat uninstall_mdatp_yum.yml
        - hosts: servers
        tasks:
            - yum:
                name: mdatp
                state: absent
        ```

## Deployment

Now run the tasks files under `/etc/ansible/playbooks/`

- Installation

    `# ansible-playbook /etc/ansible/playbooks/install_mdatp.yml -i /etc/ansible/hosts`

- Validation / Configuration

    `# ansible -m shell -a 'mdatp --connectivity-test' all`<br/>
    `# ansible -m shell -a 'mdatp --health' all`

- Un-Installation

    `# ansible-playbook /etc/ansible/playbooks/uninstall_mdatp.yml -i /etc/ansible/hosts`

## References

- [Add or remove YUM repositories](https://docs.ansible.com/ansible/2.3/yum_repository_module.html)

- [Manage packages with the yum package manager](https://docs.ansible.com/ansible/latest/modules/yum_module.html)

- [Add and remove APT repositories](https://docs.ansible.com/ansible/latest/modules/apt_repository_module.html)

- [Manage apt-packages](https://docs.ansible.com/ansible/latest/modules/apt_module.html)