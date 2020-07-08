---
title: Onboard Windows servers to the Microsoft Defender ATP service
description: Onboard Windows servers so that they can send sensor data to the Microsoft Defender ATP sensor.
keywords: onboard server, server, 2012r2, 2016, 2019, server onboarding, device management, configure Windows ATP servers, onboard Microsoft Defender Advanced Threat Protection servers
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
---

# Onboard Windows servers to the Microsoft Defender ATP service

**Applies to:**

- Windows Server 2008 R2 SP1
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server (SAC) version 1803 and later
- Windows Server 2019 and later
- Windows Server 2019 core edition
- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)](https://go.microsoft.com/fwlink/p/?linkid=2069559)

> Want to experience Microsoft Defender ATP? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-configserver-abovefoldlink)


Microsoft Defender ATP extends support to also include the Windows Server operating system. This support provides advanced attack detection and investigation capabilities seamlessly through the Microsoft Defender Security Center console.

The service supports the onboarding of the following Windows servers:
- Windows Server 2008 R2 SP1
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server (SAC) version 1803 and later
- Windows Server 2019 and later
- Windows Server 2019 core edition

For a practical guidance on what needs to be in place for licensing and infrastructure, see [Protecting Windows Servers with Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/What-s-New/Protecting-Windows-Server-with-Windows-Defender-ATP/m-p/267114#M128).

For guidance on how to download and use Windows Security Baselines for Windows servers, see [Windows Security Baselines](https://docs.microsoft.com/windows/device-security/windows-security-baselines).


## Windows Server 2008 R2 SP1, Windows Server 2012 R2, and Windows Server 2016

You can onboard Windows Server 2008 R2 SP1, Windows Server 2012 R2, and Windows Server 2016 to Microsoft Defender ATP by using any of the following options:

- **Option 1**: [Onboard through Microsoft Defender Security Center](#option-1-onboard-windows-servers-through-microsoft-defender-security-center)
- **Option 2**: [Onboard through Azure Security Center](#option-2-onboard-windows-servers-through-azure-security-center)
- **Option 3**: [Onboard through Microsoft Endpoint Configuration Manager version 2002 and later (only for Windows Server 2012 R2 and Windows Server 2016)](#option-3-onboard-windows-servers-through-microsoft-endpoint-configuration-manager-version-2002-and-later)

> [!NOTE]
> Microsoft defender ATP standalone server license is required, per node, in order to onboard a Windows server through Microsoft Defender Security Center (Option 1), or an Azure Security Center Standard license is required, per node, in order to onboard a Windows server through Azure Security Center (Option 2), see [Supported features available in Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-services).


### Option 1: Onboard Windows servers through Microsoft Defender Security Center
Perform the following steps to onboard Windows servers through Microsoft Defender Security Center:

 - For Windows Server 2008 R2 SP1 or Windows Server 2012 R2, ensure that you install the following hotfix:
    - [Update for customer experience and diagnostic telemetry](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)

 - In addition, for Windows Server 2008 R2 SP1, ensure that you fulfill the following requirements:
    - Install the [February monthly update rollup](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
    - Install either [.NET framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) (or later) or [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework)

 - For Windows Server 2008 R2 SP1 and Windows Server 2012 R2: [Configure and update System Center Endpoint Protection clients](#configure-and-update-system-center-endpoint-protection-clients).

    > [!NOTE]
    > This step is required only if your organization uses System Center Endpoint Protection (SCEP) and you're onboarding Windows Server 2008 R2 SP1 and Windows Server 2012 R2.

 - [Turn on server monitoring from Microsoft Defender Security Center](#turn-on-server-monitoring-from-the-microsoft-defender-security-center-portal).

 - If you're already leveraging System Center Operations Manager (SCOM) or Azure Monitor (formerly known as Operations Management Suite (OMS)), attach the Microsoft Monitoring Agent (MMA) to report to your Microsoft Defender ATP workspace through Multihoming support.

    Otherwise, [install and configure MMA to report sensor data to Microsoft Defender ATP](#install-and-configure-microsoft-monitoring-agent-mma-to-report-sensor-data-to-microsoft-defender-atp). For more information, see [Collect log data with Azure Log Analytics agent](https://docs.microsoft.com/azure/azure-monitor/platform/log-analytics-agent).

> [!TIP]
> After onboarding the device, you can choose to run a detection test to verify that it is properly onboarded to the service. For more information, see [Run a detection test on a newly onboarded Microsoft Defender ATP endpoint](run-detection-test.md).

### Configure and update System Center Endpoint Protection clients

Microsoft Defender ATP integrates with System Center Endpoint Protection. The integration provides visibility to malware detections and to stop propagation of an attack in your organization by banning potentially malicious files or suspected malware.

The following steps are required to enable this integration:
- Install the [January 2017 anti-malware platform update for Endpoint Protection clients](https://support.microsoft.com/help/3209361/january-2017-anti-malware-platform-update-for-endpoint-protection-clie).

- Configure the SCEP client Cloud Protection Service membership to the **Advanced** setting.


### Turn on Server monitoring from the Microsoft Defender Security Center portal

1. In the navigation pane, select **Settings** > **Device management** > **Onboarding**.

2. Select **Windows Server 2008 R2 SP1, 2012 R2 and 2016** as the operating system.

3. Click **Turn on server monitoring** and confirm that you'd like to proceed with the environment setup. When the setup completes, the **Workspace ID** and **Workspace key** fields are populated with unique values. You'll need to use these values to configure the MMA agent.

<span id="server-mma"/>

### Install and configure Microsoft Monitoring Agent (MMA) to report sensor data to Microsoft Defender ATP

1. Download the agent setup file: [Windows 64-bit agent](https://go.microsoft.com/fwlink/?LinkId=828603).

2. Using the Workspace ID and Workspace key obtained in the previous procedure, choose any of the following installation methods to install the agent on the Windows server:
    - [Manually install the agent using setup](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-the-agent-using-setup) <br>
    On the **Agent Setup Options** page, choose **Connect the agent to Azure Log Analytics (OMS)**.
    - [Install the agent using the command line](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#install-the-agent-using-the-command-line) and [configure the agent using a script](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#add-a-workspace-using-a-script).

3. You'll need to configure proxy settings for the Microsoft Monitoring Agent. For more information, see [Configure proxy settings](configure-proxy-internet.md).

Once completed, you should see onboarded Windows servers in the portal within an hour.

<span id="server-proxy"/>

### Configure Windows server proxy and Internet connectivity settings

- Each Windows server must be able to connect to the Internet using HTTPS. This connection can be direct, using a proxy, or through the <a href="https://docs.microsoft.com/azure/log-analytics/log-analytics-oms-gateway" data-raw-source="[OMS Gateway](https://docs.microsoft.com/azure/log-analytics/log-analytics-oms-gateway)">OMS Gateway</a>.
- If a proxy or firewall is blocking all traffic by default and allowing only specific domains through or HTTPS scanning (SSL inspection) is enabled, make sure that you [enable access to Microsoft Defender ATP service URLs](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

### Option 2: Onboard Windows servers through Azure Security Center
1. In the Microsoft Defender Security Center navigation pane, select **Settings** > **Device management** > **Onboarding**.

2. Select **Windows Server 2008 R2 SP1, 2012 R2 and 2016** as the operating system.

3. Click **Onboard Servers in Azure Security Center**.

4. Follow the onboarding instructions in [Microsoft Defender Advanced Threat Protection with Azure Security Center](https://docs.microsoft.com/azure/security-center/security-center-wdatp).

### Option 3: Onboard Windows servers through Microsoft Endpoint Configuration Manager version 2002 and later
You can onboard Windows Server 2012 R2 and Windows Server 2016 by using Microsoft Endpoint Configuration Manager version 2002 and later. For more information, see [Microsoft Defender Advanced Threat Protection in Microsoft Endpoint Configuration Manager current branch](https://docs.microsoft.com/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection).

## Windows Server (SAC) version 1803, Windows Server 2019, and Windows Server 2019 Core edition
You can onboard Windows Server (SAC) version 1803, Windows Server 2019, or Windows Server 2019 Core edition by using the following deployment methods:

- [Local script](configure-endpoints-script.md) 
- [Group Policy](configure-endpoints-gp.md)
- [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md#onboard-windows-10-devices-using-microsoft-endpoint-configuration-manager-current-branch)
- [System Center Configuration Manager 2012 / 2012 R2  1511 / 1602](configure-endpoints-sccm.md#onboard-windows-10-devices-using-earlier-versions-of-system-center-configuration-manager)
- [VDI onboarding scripts for non-persistent devices](configure-endpoints-vdi.md)

> [!NOTE]
> - The Onboarding package for Windows Server 2019 through Microsoft Endpoint Configuration Manager currently ships a script. For more information on how to deploy scripts in Configuration Manager, see [Packages and programs in Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs).
> - A local script is suitable for a proof of concept but should not be used for production deployment. For a production deployment, we recommend using Group Policy, Microsoft Endpoint Configuration Manager, or Intune.

Support for Windows Server, provide deeper insight into activities happening on the Windows server, coverage for kernel and memory attack detection, and enables response actions on Windows Server endpoint as well.

1. Configure Microsoft Defender ATP onboarding settings on the Windows server. For more information, see [Onboard Windows 10 devices](configure-endpoints.md).

2. If you're running a third-party antimalware solution, you'll need to apply the following Microsoft Defender AV passive mode settings. Verify that it was configured correctly:

    1. Set the following registry entry:
       - Path: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
       - Name: ForceDefenderPassiveMode
       - Type: REG_DWORD
       - Value: 1

    1. Run the following PowerShell command to verify that the passive mode was configured:

       ```PowerShell
       Get-WinEvent -FilterHashtable @{ProviderName="Microsoft-Windows-Sense" ;ID=84}
       ```

    1. Confirm  that a recent event containing the passive mode event is found:

       ![Image of passive mode verification result](images/atp-verify-passive-mode.png)

3. Run the following command to check if Microsoft Defender AV is installed:

   ```sc.exe query Windefend```

    If the result is 'The specified service does not exist as an installed service', then you'll need to install Microsoft Defender AV. For more information, see [Microsoft Defender Antivirus in Windows 10](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10).
    
    For information on how to use Group Policy to configure and manage Microsoft Defender Antivirus on your Windows servers, see [Use Group Policy settings to configure and manage Microsoft Defender Antivirus](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus).

## Integration with Azure Security Center
Microsoft Defender ATP can integrate with Azure Security Center to provide a comprehensive Windows server protection solution. With this integration, Azure Security Center can leverage the power of Microsoft Defender ATP to provide improved threat detection for Windows Servers.

The following capabilities are included in this integration:
- Automated onboarding - Microsoft Defender ATP sensor is automatically enabled on Windows Servers that are onboarded to Azure Security Center. For more information on Azure Security Center onboarding, see [Onboarding to Azure Security Center Standard for enhanced security](https://docs.microsoft.com/azure/security-center/security-center-onboarding).

    > [!NOTE]
    > Automated onboarding is only applicable for Windows Server 2008 R2 SP1, Windows Server 2012 R2, and Windows Server 2016.

- Windows servers monitored by Azure Security Center will also be available in Microsoft Defender ATP - Azure Security Center seamlessly connects to the Microsoft Defender ATP tenant, providing a single view across clients and servers.  In addition, Microsoft Defender ATP alerts will be available in the Azure Security Center console.
- Server investigation -  Azure Security Center customers can access Microsoft Defender Security Center to perform detailed investigation to uncover the scope of a potential breach.

> [!IMPORTANT]
> - When you use Azure Security Center to monitor servers, a Microsoft Defender ATP tenant is automatically created (in the US for US users, in the EU for European and UK users).
> - If you use Microsoft Defender ATP before using Azure Security Center, your data will be stored in the location you specified when you created your tenant even if you integrate with Azure Security Center at a later time.
> - When you use Azure Security Center to monitor Windows servers, a Microsoft Defender ATP tenant is automatically created and the Microsoft Defender ATP data is stored in Europe by default. If you need to move your data to another location, you need to contact Microsoft Support to reset the tenant. Server endpoint monitoring utilizing this integration has been disabled for Office 365 GCC customers.

## Offboard Windows servers
You can offboard Windows Server (SAC), Windows Server 2019, and Windows Server 2019 Core edition in the same method available for Windows 10 client devices.

For other Windows server versions, you have two options to offboard Windows servers from the service:
- Uninstall the MMA agent
- Remove the Microsoft Defender ATP workspace configuration

> [!NOTE]
> Offboarding causes the Windows server to stop sending sensor data to the portal but data from the Windows server, including reference to any alerts it has had will be retained for up to 6 months.

### Uninstall Windows servers by uninstalling the MMA agent
To offboard the Windows server, you can uninstall the MMA agent from the Windows server or detach it from reporting to your Microsoft Defender ATP workspace. After offboarding the agent, the Windows server will no longer send sensor data to Microsoft Defender ATP.
For more information, see [To disable an agent](https://docs.microsoft.com/azure/log-analytics/log-analytics-windows-agents#to-disable-an-agent).

### Remove the Microsoft Defender ATP workspace configuration
To offboard the Windows server, you can use either of the following methods:

- Remove the Microsoft Defender ATP workspace configuration from the MMA agent
- Run a PowerShell command to remove the configuration

#### Remove the Microsoft Defender ATP workspace configuration from the MMA agent

1. In the **Microsoft Monitoring Agent Properties**, select the **Azure Log Analytics (OMS)** tab.

2. Select the Microsoft Defender ATP workspace, and click **Remove**.

    ![Image of Microsoft Monitoring Agen Properties](images/atp-mma.png)

#### Run a PowerShell command to remove the configuration

1. Get your Workspace ID:

   1. In the navigation pane, select **Settings** > **Onboarding**.

   1. Select **Windows Server 2008 R2 SP1, 2012 R2 and 2016** as the operating system and get your Workspace ID:

      ![Image of Windows server onboarding](images/atp-server-offboarding-workspaceid.png)

2. Open an elevated PowerShell and run the following command. Use the Workspace ID you obtained and replacing `WorkspaceID`:

    ```powershell
    # Load agent scripting object
    $AgentCfg = New-Object -ComObject AgentConfigManager.MgmtSvcCfg
    # Remove OMS Workspace
    $AgentCfg.RemoveCloudWorkspace($WorkspaceID)
    # Reload the configuration and apply changes
    $AgentCfg.ReloadConfiguration()
    ```
## Related topics
- [Onboard Windows 10 devices](configure-endpoints.md)
- [Onboard non-Windows devices](configure-endpoints-non-windows.md)
- [Configure proxy and Internet connectivity settings](configure-proxy-internet.md)
- [Run a detection test on a newly onboarded Microsoft Defender ATP device](run-detection-test.md)
- [Troubleshooting Microsoft Defender Advanced Threat Protection onboarding issues](troubleshoot-onboarding.md)
