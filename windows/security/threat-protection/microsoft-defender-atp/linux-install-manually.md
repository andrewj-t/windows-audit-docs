---
title: Installing Microsoft Defender ATP for Linux manually
ms.reviewer: 
description: Describes how to install Microsoft Defender ATP for Linux manually, from the command line.
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

# Manual deployment

**Applies to:**

- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) for Linux](microsoft-defender-atp-linux.md)

This topic describes how to deploy Microsoft Defender ATP for Linux manually. A successful deployment requires the completion of all of the following steps:

- [Configure Microsoft's Linux Software Repository](#configure-microsoft-linux-software-repository)
- [Download onboarding packages](#download-onboarding-package)
- [Application installation](#application-installation)
- [Client configuration](#client-configuration)

## Prerequisites and system requirements

Before you get started, see [the main Microsoft Defender ATP for Linux page](microsoft-defender-atp-linux.md) for a description of prerequisites and system requirements for the current software version.

## Configure Microsoft Linux Software Repository

Microsoft Defender ATP for Linux can be deployed from one of the following channels (denoted below as *[channel]*): *insider-fast* or *prod*. Each of these channels corresponds to a Linux software repository. Instructions for configuring your device to use this repository are provided below.

The choice of the channel determines the type and frequency of updates that are offered to your device. Devices in *insider-fast* can try out new features before devices in *prod*.

In order to preview new features and provide early feedback, it is recommended that you configure some devices in your enterprise to use the *insider-fast* channel.

### RHEL and variants (CentOS and Oracle EL)

- Note your distribution and version and identify the closest entry for it under `https://packages.microsoft.com/config/`

    In the below commands, replace *[distro]* and *[version]* with the information identified in the previous step:

    > [!NOTE]
    > In case of Oracle EL and CentOS 8, use *[distro]* as “rhel”.

    ```bash
    $ sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/[distro]/[version]/[channel].repo 
    ```

    For example, if you are running CentOS 7 and wish to deploy MDATP for Linux from the *insider-fast* channel:  

    ```bash
    $ sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/centos/7/insiders-fast.repo 
    ```

- Install the Microsoft GPG public key:

    ```bash
    $ curl https://packages.microsoft.com/keys/microsoft.asc > microsoft.asc
    $ sudo rpm --import microsoft.asc
    ```

- Download and make usable all the metadata for the currently enabled yum repositories: 

    ```bash
    $ yum makecache
    ```

### SLES and variants

- Note your distribution and version and identify the closest entry for it under `https://packages.microsoft.com/config/`

    In the below commands, replace *[distro]* and *[version]* with the information identified in the previous step.

    ```bash
    $ sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo 
    ```

    For example, if you are running SLES 12 and wish to deploy MDATP for Linux from the *insider-fast* channel:  

    ```bash
    $ sudo zypper addrepo -c -f -n microsoft-insiders-fast https://packages.microsoft.com/config/sles/12/insiders-fast.repo
    ```

- Install the Microsoft GPG public key:

    ```bash
    $ curl https://packages.microsoft.com/keys/microsoft.asc > microsoft.asc
    $ rpm --import microsoft.asc
    ```

### Ubuntu and Debian systems

- Install `‘curl’` if not already installed:

    ```bash
    $ sudo apt-get install curl
    ```

- Note your distribution and version and identify the closest entry for it under `https://packages.microsoft.com/config`

    In the below command, replace *[distro]* and *[version]* with the information identified in the previous step:

    ```bash
    $ curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
    ```

    For example, if you are running Ubuntu 18.04 and wish to deploy MDATP for Linux from the *insider-fast* channel:

    ```bash
    $ curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/insiders-fast.list 
    ```

- Install the repository configuration:

    ```bash
    $ sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

- Install the gpg package if not already installed:

    ```bash
    $ sudo apt-get install gpg
    ```

- Install the Microsoft GPG public key:

    ```bash
    $ curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
    $ sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/

    ```

- Install the https driver in case not already present:

    ```bash
    $ sudo apt-get install apt-transport-https
    ```

- Update the repository metadata

    ```bash
    $ sudo apt-get update
    ```

## Application installation

- RHEL and variants (CentOS and Oracle EL)

    ```bash
    sudo yum install mdatp
    ```

- SLES and variants

    ```bash
    sudo zypper install mdatp
    ```

- Ubuntu and Debian system

    ```bash
    sudo apt-get install mdatp
    ```

## Download onboarding package

Download the onboarding package from Microsoft Defender Security Center:

1. In Microsoft Defender Security Center, go to **Settings > Machine Management > Onboarding**.
2. In Section 1 of the page, set operating system to **Linux Server** and Deployment method to **Local script**.
3. In Section 2 of the page, select **Download onboarding package**. Save it as WindowsDefenderATPOnboardingPackage.zip.

    ![Microsoft Defender Security Center screenshot](images/atp-portal-onboarding-linux.png)

4. From a command prompt, verify that you have the file.
    Extract the contents of the archive:
  
    ```bash
    $ ls -l
    total 8
    -rw-r--r-- 1 test  staff  5752 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip

    $ unzip WindowsDefenderATPOnboardingPackage.zip
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: WindowsDefenderATPOnboarding.py
    ```

## Client configuration

1. Copy WindowsDefenderATPOnboarding.py to the target machine.

    Initially the client machine is not associated with an organization. Note that the *orgId* attribute is blank.

    ```bash
    $ mdatp --health orgId
    ```

2. Run WindowsDefenderATPOnboarding.py (note that in order to run this command you must have `python` installed on the device).

    ```bash
    $ python WindowsDefenderATPOnboarding.py
    ```

3. Verify that the machine is now associated with your organization and reports a valid organization identifier:

    ```bash
    $ mdatp --health orgId
    [your organization identifier]
    ```

4. A few minutes following the completion of the installation, you can see the status by running the following command. A return value of `1` denotes that the product is functioning as expected.

    ```bash
    $ mdatp --health healthy
    1
    ```

5. Run a detection test to verify that the machine is properly onboarded and reporting to the service. Perform the following steps on the newly onboarded machine:

    - Ensure that real-time protection is enabled (denoted by a result of `1` from running the following command).

    ```bash
    $ mdatp --health realTimeProtectionEnabled
    1
    ```

    - Open a Terminal window
Copy and run the command below:

    ``` bash
    $ curl -o ~/Downloads/eicar.com.txt http://www.eicar.org/download/eicar.com.txt
    ```

    - The file should have been quarantined by Microsoft Defender ATP for Linux. Use the following command to list all the detected threats:

    ```bash
    $ mdatp --threat --list --pretty
    ```

## Logging installation issues

See [Logging installation issues](linux-resources.md#logging-installation-issues) for more information on how to find the automatically generated log that is created by the installer when an error occurs.

## Uninstallation

See [Uninstalling](linux-resources.md#uninstalling) for details on how to remove Microsoft Defender ATP for Linux from client devices.
