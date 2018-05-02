---
title: Enable Block at First Sight to detect malware in seconds
description: Enable the Block at First sight feature to detect and block malware within seconds, and validate that it is configured correctly.
keywords: scan, BAFS, malware, first seen, first sight, cloud, defender
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: andreabichsel
ms.author: v-anbic
ms.date: 05/02/2018
---

# Enable the Block at First Sight feature

**Applies to**

- Windows 10, version 1703 and later

**Audience**

- Enterprise security administrators

**Manageability available with**

- Intune
- Group Policy
- Windows Defender Security Center app


Block at first sight is a feature of Windows Defender Antivirus cloud-delivered protection that provides a way to detect and block new malware within seconds. 

It is enabled by default when certain pre-requisite settings are also enabled. In most cases, these pre-requisite settings are also enabled by default, so the feature is running without any intervention. You can use group policy settings to confirm the feature is enabled.

You can [specify how long the file should be prevented from running](configure-cloud-block-timeout-period-windows-defender-antivirus.md) while the cloud-based protection service analyzes the file.

You can also [customize the message displayed on users' desktops](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) when a file is blocked. You can change the company name, contact information, and message URL.

> [!IMPORTANT]
> There is no specific individual setting in System Center Configuration Manager to enable or disable Block at First Sight. It is enabled by default when the pre-requisite settings are configured correctly. You must use Group Policy settings to enable or disable the feature.


>[!TIP]
>You can also visit the Windows Defender Testground website at [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) to confirm the features are working and see how they work.


## How it works

When a Windows Defender Antivirus client encounters a suspicious but undetected file, it queries our cloud protection backend. The cloud backend will apply heuristics, machine learning, and automated analysis of the file to determine the files as malicious or clean. 

In Windows 10, version 1803, the Block at First Sight feature can now block non-portable executable files (such as JS, VBS, or macros) as well as executable files.

The Block at First Sight feature only uses the cloud protection backend for executable files and non-portable executable files that are downloaded from the Internet, or originating from the Internet zone. A hash value of the .exe file is checked via the cloud backend to determine if this is a previously undetected file.

If the cloud backend is unable to make a determination, the file will be locked by Windows Defender AV while a copy is uploaded to the cloud. The cloud will perform additional analysis to reach a determination before it allows the file to run or blocks it in all future encounters, depending on whether the file is determined to be malicious or safe. 

In many cases this process can reduce the response time for new malware from hours to seconds.


## Confirm and validate Block at First Sight is enabled

Block at First Sight requires a number of Group Policy settings to be configured correctly or it will not work. Usually, these settings are already enabled in most default Windows Defender AV deployments in enterprise networks.

### Confirm Block at First Sight is enabled with Intune

1. In Intune, navigate to **Device configuration - Profiles | *Profile name* | Device restrictions | Windows Defender Antivirus**.

	> [!NOTE]
	> The profile you select must be a Device Restriction profile type, not an Endpoint Protection profile type.

2. Verify these settings are configured as follows:

	- **Cloud-delivered protection**: **Enable**
	- **File Blocking Level**: **High**
	- **Time extension for file scanning by the cloud**: **50**
	- **Prompt users before sample submission**: **Send all data without prompting**

For more information about configuring Windows Defender AV device restrictions in Intune, see [Configure device restriction settings in Microsoft Intune](https://docs.microsoft.com/en-us/intune/device-restrictions-configure).

For a list of Windows Defender AV device restrictions in Intune, see [Device restriction for Windows 10 (and newer) settings in Intune](https://docs.microsoft.com/en-us/intune/device-restrictions-windows-10#windows-defender-antivirus).


### Confirm Block at First Sight is enabled with Group Policy

1.  On your Group Policy management machine, open the [Group Policy Management Console](https://technet.microsoft.com/library/cc731212.aspx), right-click the Group Policy Object you want to configure and click **Edit**.

3.  In the **Group Policy Management Editor** go to **Computer configuration** and click **Administrative templates**.

5.  Expand the tree to **Windows components > Windows Defender Antivirus > MAPS** and configure the following Group Policies:
    
    1.  Double-click the **Join Microsoft MAPS** setting and ensure the option is set to **Enabled**. Click **OK**.
    
    1.  Double-click the **Send file samples when further analysis is required** setting and ensure the option is set to **Enabled** and the additional options are either of the following:
    
        1. Send safe samples (1)
        
        1. Send all samples (3)

        > [!WARNING]
        > Setting to 0 (Always Prompt) will lower the protection state of the device. Setting to 2 (Never send) means the "Block at First Sight" feature will not function.

    1. Click **OK**.

1.  In the **Group Policy Management Editor**, expand the tree to **Windows components > Windows Defender Antivirus > Real-time Protection**:
    
    1.  Double-click the **Scan all downloaded files and attachments** setting and ensure the option is set to **Enabled**. Click **OK**.
    
    1.  Double-click the **Turn off real-time protection** setting and ensure the option is set to **Disabled**. Click **OK**.

If you had to change any of the settings, you should re-deploy the Group Policy Object across your network to ensure all endpoints are covered.


### Confirm Block at First Sight is enabled with the Windows Defender Security Center app

You can confirm that Block at First Sight is enabled in Windows Settings. 

The feature is automatically enabled as long as **Cloud-based protection** and **Automatic sample submission** are both turned on.

**Confirm Block at First Sight is enabled on individual clients**

1. Open the Windows Defender Security Center app by clicking the shield icon in the task bar or searching the start menu for **Defender**.

2. Click the **Virus & threat protection** tile (or the shield icon on the left menu bar) and then the **Virus & threat protection settings** label:

 ![Screenshot of the Virus & threat protection settings label in the Windows Defender Security Center app](images/defender/wdav-protection-settings-wdsc.png)
    
3.	Confirm that **Cloud-based Protection** and **Automatic sample submission** are switched to **On**.

> [!NOTE]
> If the pre-requisite settings are configured and deployed using Group Policy, the settings described in this section will be greyed-out and unavailable for use on individual endpoints. Changes made through a Group Policy Object must first be deployed to individual endpoints before the setting will be updated in Windows Settings.


### Validate Block at First Sight is working

You can validate that the feature is working by following the steps outlined in the [Validate connections between your network and the cloud](configure-network-connections-windows-defender-antivirus.md#validate) topic.


## Disable Block at First Sight

> [!WARNING]
> Disabling the Block at First Sight feature will lower the protection state of the endpoint and your network.

You may choose to disable the Block at First Sight feature if you want to retain the pre-requisite settings without using Block at First Sight protection. You might wish to do this if you are experiencing latency issues or you want to test the feature's impact on your network.

**Disable Block at First Sight with Group Policy**

1.  On your Group Policy management machine, open the [Group Policy Management Console](https://technet.microsoft.com/library/cc731212.aspx), right-click the Group Policy Object you want to configure and click **Edit**.

3.  In the **Group Policy Management Editor** go to **Computer configuration** and click **Administrative templates**.

5.  Expand the tree through **Windows components > Windows Defender Antivirus > MAPS**.

1.  Double-click the **Configure the 'Block at First Sight' feature** setting and set the option to **Disabled**.

    > [!NOTE]
    > Disabling the Block at First Sight feature will not disable or alter the pre-requisite group policies.


## Related topics

- [Windows Defender in Windows 10](windows-defender-antivirus-in-windows-10.md)
- [Enable cloud-delivered protection](enable-cloud-protection-windows-defender-antivirus.md)


