---
title: Enable Block at First Sight to detect malware in seconds
description: Turn on the block at first sight feature to detect and block malware within seconds, and validate that it is configured correctly.
keywords: scan, BAFS, malware, first seen, first sight, cloud, defender
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.reviewer: 
manager: dansimp
ms.custom: nextgen
ms.date: 10/15/2020
---

# Turn on block at first sight

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Applies to:**

- Microsoft Defender Antivirus

Block at first sight provides a way to detect and block new malware within seconds. This protection is enabled by default when certain prerequisite settings are also enabled. In most cases, these prerequisite settings are also enabled by default, so the feature is running without any intervention. 

You can [specify how long the file should be prevented from running](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) while the cloud-based protection service analyzes the file. And, you can [customize the message displayed on users' desktops](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) when a file is blocked. You can change the company name, contact information, and message URL.

>[!TIP]
>Visit the Microsoft Defender ATP demo website at [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) to confirm the features are working and see how they work.

## How it works

When Microsoft Defender Antivirus encounters a suspicious but undetected file, it queries our cloud protection backend. The cloud backend applies heuristics, machine learning, and automated analysis of the file to determine whether the files are malicious or not a threat.

Microsoft Defender Antivirus uses multiple detection and prevention technologies to deliver accurate, intelligent, and real-time protection. To learn more, see this blog: [Get to know the advanced technologies at the core of Microsoft Defender ATP next-generation protection](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/).
![List of Microsoft Defender AV engines](images/microsoft-defender-atp-next-generation-protection-engines.png)  

In Windows 10, version 1803 or later, block at first sight can block non-portable executable files (such as JS, VBS, or macros) as well as executable files.

Block at first sight only uses the cloud protection backend for executable files and non-portable executable files that are downloaded from the Internet, or that originate from the Internet zone. A hash value of the .exe file is checked via the cloud backend to determine if this is a previously undetected file.

If the cloud backend is unable to make a determination, Microsoft Defender Antivirus locks the file and uploads a copy to the cloud. The cloud performs additional analysis to reach a determination before it either allows the file to run or blocks it in all future encounters, depending on whether it determines the file to be malicious or safe.

In many cases, this process can reduce the response time for new malware from hours to seconds.

## Confirm and validate that block at first sight is turned on

Block at first sight requires a number of settings to be configured correctly or it will not work. These settings are enabled by default in most enterprise Microsoft Defender Antivirus deployments.

### Confirm block at first sight is turned on with Intune

1. In Intune, navigate to **Device configuration - Profiles** > *Profile name* > **Device restrictions** > **Microsoft Defender Antivirus**.

   > [!NOTE]
   > The profile you select must be a Device Restriction profile type, not an Endpoint Protection profile type.

2. Verify these settings are configured as follows:

   - **Cloud-delivered protection**: **Enable**
   - **File Blocking Level**: **High**
   - **Time extension for file scanning by the cloud**: **50**
   - **Prompt users before sample submission**: **Send all data without prompting**

   ![Intune config](images/defender/intune-block-at-first-sight.png)

   > [!WARNING]
   > Setting the file blocking level to **High** will apply a strong level of detection. In the unlikely event that it causes a false positive detection of legitimate files, use the option to [restore the quarantined files](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/restore-quarantined-files-microsoft-defender-antivirus).

For more information about configuring Microsoft Defender Antivirus device restrictions in Intune, see [Configure device restriction settings in Microsoft Intune](https://docs.microsoft.com/intune/device-restrictions-configure).

For a list of Microsoft Defender Antivirus device restrictions in Intune, see [Device restriction for Windows 10 (and newer) settings in Intune](https://docs.microsoft.com/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

### Turn on block at first sight with Microsoft Endpoint Configuration Manager

1. In Microsoft Endpoint Configuration Manager, click **Assets and Compliance** > **Endpoint Protection** > **AntiMalware Policies**.

2. Click **Home** > **Create Antimalware Policy**.

3. Enter a name and a description, and add these settings:
   - **Real time protection**
   - **Advanced**
   - **Cloud Protection Service**

4. In the left column, click **Real time protection**, set **Enable real-time protection** to **Yes**, and set **Scan system files** to **Scan incoming and outgoing files**.
   ![Enable real-time protection](images/defender/sccm-real-time-protection.png)

5. Click **Advanced**, set **Enable real-time protection** to **Yes**, and set **Scan system files** to **Scan incoming and outgoing files**.
   ![Enable Advanced settings](images/defender/sccm-advanced-settings.png)

6. Click **Cloud Protection Service**, set **Cloud Protection Service membership type** to **Advanced membership**, set **Level for blocking suspicious files** to **High**, and set **Allow extended cloud check to block and scan suspicious files for up to (seconds)** to **50** seconds.
   ![Enable Cloud Protection Service](images/defender/sccm-cloud-protection-service.png)

7. Click **OK** to create the policy.

### Confirm block at first sight is turned on with Group Policy

1. On your Group Policy management computer, open the [Group Policy Management Console](https://technet.microsoft.com/library/cc731212.aspx), right-click the Group Policy Object you want to configure and click **Edit**. 

2. In the **Group Policy Management Editor** go to **Computer configuration** and click **Administrative templates**.

3. Expand the tree to **Windows components** > **Microsoft Defender Antivirus** > **MAPS**, configure the following Group Policies, and then click **OK**:

    1. Double-click **Join Microsoft MAPS** and ensure the option is set to **Enabled**. Click **OK**.

    2. Double-click **Send file samples when further analysis is required** and ensure the option is set to **Enabled** and the additional options are either **Send safe samples (1)** or **Send all samples (3)**.

    > [!WARNING]
    > Setting to **Always prompt (0)** will lower the protection state of the device. Setting to **Never send (2)** means block at first sight will not function.

4. In the **Group Policy Management Editor**, expand the tree to **Windows components** > **Microsoft Defender Antivirus** > **Real-time Protection**:

    1. Double-click **Scan all downloaded files and attachments** and ensure the option is set to **Enabled**, and then click **OK**.

    2. Double-click **Turn off real-time protection** and ensure the option is set to **Disabled**, and then click **OK**.

5. In the **Group Policy Management Editor**, expand the tree to **Windows components** > **Microsoft Defender Antivirus** > **MpEngine**:

    1. Double-click **Select cloud protection level** and ensure the option is set to **Enabled**. 

    2. Ensure that **Select cloud blocking level** section on the same page is set to **High blocking level**, and then click **OK**.
    
If you had to change any of the settings, you should redeploy the Group Policy Object across your network to ensure all endpoints are covered.

### Confirm block at first sight is turned on with Registry editor

1. Start Registry Editor.

2. Go to `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows Defender\Spynet`, and make sure that 

    1. **SpynetReporting** key is set to **1**

    2. **SubmitSamplesConsent** key is set to either **1** (Send safe samples) or **3** (Send all samples)

3. Go to `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows Defender\Real-Time Protection`, and make sure that

    1. **DisableIOAVProtection** key is set to **0**

    2. **DisableRealtimeMonitoring** key is set to **0**
    
4. Go to `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows Defender\MpEngine`, and make sure that the **MpCloudBlockLevel** key is set to **2**
    
### Confirm Block at First Sight is enabled on individual clients

You can confirm that block at first sight is enabled on individual clients using Windows security settings.

Block at first sight is automatically enabled as long as **Cloud-delivered protection** and **Automatic sample submission** are both turned on.

1. Open the Windows Security app.

2. Select **Virus & threat protection**, and then, under **Virus & threat protection settings**, select **Manage Settings**.

   ![Screenshot of the Virus & threat protection settings label in the Windows Security app](images/defender/wdav-protection-settings-wdsc.png)

3. Confirm that **Cloud-delivered protection** and **Automatic sample submission** are both turned on.

> [!NOTE]
> If the prerequisite settings are configured and deployed using Group Policy, the settings described in this section will be greyed-out and unavailable for use on individual endpoints. Changes made through a Group Policy Object must first be deployed to individual endpoints before the setting will be updated in Windows Settings.

### Validate block at first sight is working

You can validate that the feature is working by following the steps outlined in [Validate connections between your network and the cloud](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud).

## Turn off block at first sight

> [!WARNING]
> Turning off block at first sight will lower the protection state of the endpoint and your network.

You may choose to disable block at first sight if you want to retain the prerequisite settings without using block at first sight protection. You might wish to do this if you are experiencing latency issues or you want to test the feature's impact on your network.

### Turn off block at first sight with Group Policy

1. On your Group Policy management computer, open the [Group Policy Management Console](https://technet.microsoft.com/library/cc731212.aspx), right-click the Group Policy Object you want to configure, and then click **Edit**.

2. In the **Group Policy Management Editor** go to **Computer configuration** and click **Administrative templates**.

3. Expand the tree through **Windows components** > **Microsoft Defender Antivirus** > **MAPS**.

4. Double-click **Configure the 'Block at First Sight' feature** and set the option to **Disabled**.

    > [!NOTE]
    > Disabling block at first sight does not disable or alter the prerequisite group policies.

## See also

- [Microsoft Defender Antivirus in Windows 10](microsoft-defender-antivirus-in-windows-10.md)

- [Enable cloud-delivered protection](enable-cloud-protection-microsoft-defender-antivirus.md)
