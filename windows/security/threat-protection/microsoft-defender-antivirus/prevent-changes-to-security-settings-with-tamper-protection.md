---
title: Protect security settings with tamper protection
ms.reviewer: shwjha, hayhov
manager: dansimp
description: Use tamper protection to prevent malicious apps from changing important security settings.
keywords: malware, defender, antivirus, tamper protection
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/07/2021
ms.technology: mde
---

# Protect security settings with tamper protection

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Applies to:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)

Tamper protection is available on devices running the following versions of Windows:   
 
- Windows 10
- Windows Server 2016 and 2019 (if using tenant attach with [Configuration Manager, version 2006](#manage-tamper-protection-with-configuration-manager-version-2006))

## Overview

During some kinds of cyber attacks, bad actors try to disable security features, such as anti-virus protection, on your machines. Bad actors like to disable your security features to get easier access to your data, to install malware, or to otherwise exploit your data, identity, and devices. Tamper protection helps prevent these kinds of things from occurring.

With tamper protection, malicious apps are prevented from taking actions such as:

- Disabling virus and threat protection
- Disabling real-time protection
- Turning off behavior monitoring
- Disabling antivirus (such as IOfficeAntivirus (IOAV))
- Disabling cloud-delivered protection
- Removing security intelligence updates

### How it works

Tamper protection essentially locks Microsoft Defender Antivirus and prevents your security settings from being changed through apps and methods such as:

- Configuring settings in Registry Editor on your Windows machine
- Changing settings through PowerShell cmdlets
- Editing or removing security settings through group policies

Tamper protection doesn't prevent you from viewing your security settings. And, tamper protection doesn't affect how third-party antivirus apps register with the Windows Security app. If your organization is using Windows 10 Enterprise E5, individual users can't change the tamper protection setting; tamper protection is managed by your security team.

### What do you want to do?

1. Turn tamper protection on <br/>
    - [For an individual machine, use Windows Security](#turn-tamper-protection-on-or-off-for-an-individual-machine).
    - [For your organization, use Intune](#turn-tamper-protection-on-or-off-for-your-organization-using-intune).
    - [Use tenant attach with Configuration Manager, version 2006, for devices running Windows 10 or Windows Server 2019](#manage-tamper-protection-with-configuration-manager-version-2006)

2. [View information about tampering attempts](#view-information-about-tampering-attempts).

3. [Review your security recommendations](#review-your-security-recommendations).

4. [Browse the frequently asked questions](#view-information-about-tampering-attempts).

## Turn tamper protection on (or off) for an individual machine

> [!NOTE]
> Tamper protection blocks attempts to modify Microsoft Defender Antivirus settings through the registry.
>
> To help ensure that tamper protection doesn’t interfere with third-party security products or enterprise installation scripts that modify these settings, go to **Windows Security** and update **Security intelligence** to version 1.287.60.0 or later. (See [Security intelligence updates](https://www.microsoft.com/wdsi/definitions).)
>
> Once you’ve made this update, tamper protection will continue to protect your registry settings, and will also log attempts to modify them without returning errors.

If you are a home user, or you are not subject to settings managed by a security team, you can use the Windows Security app to turn tamper protection on or off. You must have appropriate admin permissions on your machine to do change security settings, such as tamper protection.

1. Click **Start**, and start typing *Security*. In the search results, select **Windows Security**.

2. Select **Virus & threat protection** > **Virus & threat protection settings**.

3. Set **Tamper Protection** to **On** or **Off**.

   Here's what you see in the Windows Security app:

   ![Tamper protection turned on in Windows 10 Home](images/tamperprotectionturnedon.png)

## Turn tamper protection on (or off) for your organization using Intune

If you are part of your organization's security team, and your subscription includes [Intune](https://docs.microsoft.com/intune/fundamentals/what-is-intune), you can turn tamper protection on (or off) for your organization in the [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com) portal.

You must have appropriate [permissions](../microsoft-defender-atp/assign-portal-access.md), such as global admin, security admin, or security operations, to perform the following task.

1. Make sure your organization meets all of the following requirements to use Intune to manage tamper protection:

    - Your organization uses [Intune to manage devices](https://docs.microsoft.com/intune/fundamentals/what-is-device-management). ([Intune licenses](https://docs.microsoft.com/intune/fundamentals/licenses) are required; Intune is included in Microsoft 365 E5.)
    - Your Windows machines must be running Windows 10 OS [1709](https://docs.microsoft.com/windows/release-health/status-windows-10-1709), [1803](https://docs.microsoft.com/windows/release-health/status-windows-10-1803), [1809](https://docs.microsoft.com/windows/release-health/status-windows-10-1809-and-windows-server-2019) or later. (For more information about releases, see [Windows 10 release information](https://docs.microsoft.com/windows/release-health/release-information).)
    - You must be using Windows security with [security intelligence](https://www.microsoft.com/wdsi/definitions) updated to version 1.287.60.0 (or above).
    - Your machines must be using anti-malware platform version 4.18.1906.3 (or above) and anti-malware engine version 1.1.15500.X (or above). ([Manage Microsoft Defender Antivirus updates and apply baselines](manage-updates-baselines-microsoft-defender-antivirus.md).)

2. Go to the [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com) and sign in with your work or school account.

3. Select **Devices** > **Configuration Profiles**.

4. Create a profile that includes the following settings:

    - **Platform: Windows 10 and later**

    - **Profile type: Endpoint protection**

    - **Category: Microsoft Defender Security Center**

    - **Tamper Protection: Enabled**

    ![Turn tamper protection on with Intune](images/turnontamperprotect-MEM.png)

5. Assign the profile to one or more groups.

### Are you using Windows OS 1709, 1803, or 1809?

If you are using Windows 10 OS [1709](https://docs.microsoft.com/windows/release-health/status-windows-10-1709), [1803](https://docs.microsoft.com/windows/release-health/status-windows-10-1803), or [1809](https://docs.microsoft.com/windows/release-health/status-windows-10-1809-and-windows-server-2019), you won't see **Tamper Protection** in the Windows Security app. In this case, you can use PowerShell to determine whether tamper protection is enabled.

#### Use PowerShell to determine whether tamper protection is turned on

1. Open the Windows PowerShell app.

2. Use the [Get-MpComputerStatus](https://docs.microsoft.com/powershell/module/defender/get-mpcomputerstatus?view=win10-ps&preserve-view=true) PowerShell cmdlet.

3. In the list of results, look for `IsTamperProtected`. (A value of *true* means tamper protection is enabled.)

## Manage tamper protection with Configuration Manager, version 2006

> [!IMPORTANT]
> The procedure can be used to extend tamper protection to devices running Windows 10 and Windows Server 2019. Make sure to review the prerequisites and other information in the resources mentioned in this procedure.

If you're using [version 2006 of Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006), you can manage tamper protection settings on Windows 10, Windows Server 2016, and Windows Server 2019 by using a method called *tenant attach*. Tenant attach enables you to sync your on-premises-only Configuration Manager devices into the Microsoft Endpoint Manager admin center, and then deliver your endpoint security configuration policies to your on-premises collections & devices.

1. Set up tenant attach. See [Microsoft Endpoint Manager tenant attach: Device sync and device actions](https://docs.microsoft.com/mem/configmgr/tenant-attach/device-sync-actions).

2. In the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Endpoint security** > **Antivirus**, and choose **+ Create Policy**.<br/> 

   - In the **Platform** list, select **Windows 10 and Windows Server (ConfigMgr)**.  
     
   - In the **Profile** list, select **Windows Security experience (preview)**. <br/>
   
   The following screenshot illustrates how to create your policy:

   :::image type="content" source="images/win-security- exp-policy-endpt-security.png" alt-text="Windows security experience in Endpoint Manager":::

3. Deploy the policy to your device collection.

Need help? See the following resources:

- [Settings for the Windows Security experience profile in Microsoft Intune](https://docs.microsoft.com/mem/intune/protect/antivirus-security-experience-windows-settings)

- [Tech Community Blog: Announcing Tamper Protection for Configuration Manager Tenant Attach clients](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)


## View information about tampering attempts

Tampering attempts typically indicate bigger cyberattacks. Bad actors try to change security settings as a way to persist and stay undetected. If you're part of your organization's security team, you can view information about such attempts, and then take appropriate actions to mitigate threats.

When a tampering attempt is detected, an alert is raised in the [Microsoft Defender Security Center](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/portal-overview) ([https://securitycenter.windows.com](https://securitycenter.windows.com)).

![Microsoft Defender Security Center](images/tamperattemptalert.png)

Using [endpoint detection and response](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) and [advanced hunting](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) capabilities in Microsoft Defender for Endpoint, your security operations team can investigate and address such attempts.

## Review your security recommendations

Tamper protection integrates with [Threat & Vulnerability Management](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) capabilities. [Security recommendations](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation) include making sure tamper protection is turned on. For example, you can search on *tamper*, as shown in the following image:

![Tamper protection results in security recommendations](../images/securityrecs-tamperprotect.jpg)

In the results, you can select **Turn on Tamper Protection** to learn more and turn it on.

![Turn on tamper protection](images/tamperprotectsecurityrecos.png)

To learn more about Threat & Vulnerability Management, see [Threat & Vulnerability Management in Microsoft Defender Security Center](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/tvm-dashboard-insights#threat--vulnerability-management-in-microsoft-defender-security-center).

## Frequently asked questions

### To which Windows OS versions is configuring tamper protection is applicable?

Windows 10 OS [1709](https://docs.microsoft.com/windows/release-health/status-windows-10-1709), [1803](https://docs.microsoft.com/windows/release-health/status-windows-10-1803), [1809](https://docs.microsoft.com/windows/release-health/status-windows-10-1809-and-windows-server-2019), or later together with [Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp).

If you are using Configuration Manager, version 2006, with tenant attach, tamper protection can be extended to Windows Server 2019. See [Tenant attach: Create and deploy endpoint security Antivirus policy from the admin center (preview)](https://docs.microsoft.com/mem/configmgr/tenant-attach/deploy-antivirus-policy).

### Will tamper protection have any impact on third-party antivirus registration?

No. Third-party antivirus offerings will continue to register with the Windows Security application.

### What happens if Microsoft Defender Antivirus is not active on a device?

Devices that are onboarded to Microsoft Defender for Endpoint will have Microsoft Defender Antivirus running in passive mode. Tamper protection will continue to protect the service and its features. 

### How can I turn tamper protection on/off?

If you are a home user, see [Turn tamper protection on (or off) for an individual machine](#turn-tamper-protection-on-or-off-for-an-individual-machine).

If you are an organization using [Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp), you should be able to manage tamper protection in Intune similar to how you manage other endpoint protection features. See the following sections of this article: 

- [Turn tamper protection on (or off) for your organization using Intune](#turn-tamper-protection-on-or-off-for-your-organization-using-intune)

- [Manage tamper protection with Configuration Manager, version 2006](#manage-tamper-protection-with-configuration-manager-version-2006) 

### How does configuring tamper protection in Intune affect how I manage Microsoft Defender Antivirus through my group policy?

Your regular group policy doesn’t apply to tamper protection, and changes to Microsoft Defender Antivirus settings are ignored when tamper protection is on. 

### For Microsoft Defender for Endpoint, is configuring tamper protection in Intune targeted to the entire organization only?

Configuring tamper protection in Intune or Microsoft Endpoint Manager can be targeted to your entire organization and to specific devices and user groups.

### Can I configure Tamper Protection in Microsoft Endpoint Configuration Manager?

If you are using tenant attach, you can use Microsoft Endpoint Configuration Manager. See [Manage tamper protection with Configuration Manager, version 2006](#manage-tamper-protection-with-configuration-manager-version-2006) and [Tech Community blog: Announcing Tamper Protection for Configuration Manager Tenant Attach clients](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin).

### I have the Windows E3 enrollment. Can I use configuring tamper protection in Intune?

Currently, configuring tamper protection in Intune is only available for customers who have [Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp).

### What happens if I try to change Microsoft Defender for Endpoint settings in Intune, Microsoft Endpoint Configuration Manager, and Windows Management Instrumentation when Tamper Protection is enabled on a device?

You won’t be able to change the features that are protected by tamper protection; such change requests are ignored.

### I’m an enterprise customer. Can local admins change tamper protection on their devices?

No. Local admins cannot change or modify tamper protection settings.

### What happens if my device is onboarded with Microsoft Defender for Endpoint and then goes into an off-boarded state?

If a device is off-boarded from Microsoft Defender for Endpoint, tamper protection is turned on, which is the default state for unmanaged devices. 

### Will there be an alert about tamper protection status changing in the Microsoft Defender Security Center?

Yes. The alert is shown in [https://securitycenter.microsoft.com](https://securitycenter.microsoft.com) under **Alerts**.

In addition, your security operations team can use hunting queries, such as the following example:

`DeviceAlertEvents | where Title == "Tamper Protection bypass"`

[View information about tampering attempts](#view-information-about-tampering-attempts).

## See also

[Help secure Windows PCs with Endpoint Protection for Microsoft Intune](https://docs.microsoft.com/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[Get an overview of Microsoft Defender for Endpoint](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp)

[Better together: Microsoft Defender Antivirus and Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md)
