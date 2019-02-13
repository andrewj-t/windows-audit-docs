---
title: Configure advanced features in Windows Defender ATP
description: Turn on advanced features such as block file in Windows Defender Advanced Threat Protection.
keywords: advanced features, settings, block file, automated investigation, auto-resolve, skype, azure atp, office 365, azure information protection, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance 
ms.topic: article
ms.date: 11/16/2018
---

# Configure advanced features in Windows Defender ATP

**Applies to:**
- [Windows Defender Advanced Threat Protection (Windows Defender ATP)](https://wincom.blob.core.windows.net/documents/Windows10_Commercial_Comparison.pdf)

>Want to experience Windows Defender ATP? [Sign up for a free trial.](https://www.microsoft.com/en-us/WindowsForBusiness/windows-atp?ocid=docs-wdatp-advancedfeats-abovefoldlink)

Depending on the Microsoft security products that you use, some advanced features might be available for you to integrate Windows Defender ATP with.

Use the following advanced features to get better protected from potentially malicious files and gain better insight during security investigations:

## Automated investigation
When you enable this feature, you'll be able to take advantage of the automated investigation and remediation features of the service. For more information, see [Automated investigations](automated-investigations-windows-defender-advanced-threat-protection.md).

## Auto-resolve remediated alerts
For tenants created on or after Windows 10, version 1809 the automated investigations capability is configured by default to resolve alerts where the automated analysis result status is "No threats found" or "Remediated".  If you don’t want to have alerts auto-resolved, you’ll need to manually turn off the feature.

>[!TIP] 
>For tenants created prior that version, you'll need to manually turn this feature on from the [Advanced features](https://securitycenter.windows.com/preferences2/integration) page.

>[!NOTE]
> - The result of the auto-resolve action may influence the Machine risk level calculation which is based on the active alerts found on a machine.  
>- If a security operations analyst manually sets the status of an alert to "In progress" or "Resolved" the auto-resolve capability will not overrite it.


## Block file
This feature is only available if your organization uses Windows Defender Antivirus as the active antimalware solution and that the cloud-based protection feature is enabled.

If your organization satisfies these conditions, the feature is enabled by default. This feature enables you to block potentially malicious files in your network. This operation will prevent it from being read, written, or executed on machines in your organization.

## Show user details
When you enable this feature, you'll be able to see user details stored in Azure Active Directory including a user's picture, name, title, and department information  when investigating user account entities. You can find user account information in the following views:
- Security operations dashboard
- Alert queue
- Machine details page

For more information, see [Investigate a user account](investigate-user-windows-defender-advanced-threat-protection.md).

## Skype for Business integration
Enabling the Skype for Business integration gives you the ability to communicate with users using Skype for Business, email, or phone. This can be handy when you need to communicate with the user and mitigate risks.

## Azure Advanced Threat Protection integration
The integration with Azure Advanced Threat Protection allows you to pivot directly into another Microsoft Identity security product. Azure Advanced Threat Protection augments an investigation with additional insights about a suspected compromised account and related resources. By enabling this feature, you'll enrich the machine-based investigation capability by pivoting across the network from an identify point of view.


>[!NOTE]
>You'll need to have the appropriate license to enable this feature. 

### Enable the Windows Defender ATP integration from the Azure ATP portal
To receive contextual machine integration in Azure ATP, you'll also need to enable the feature in the Azure ATP portal.

1. Login to the [Azure portal](https://portal.atp.azure.com/) with a Global Administrator or Security Administrator role.

2. Click **Create a workspace** or use your primary workspace.

3. Toggle the Integration setting to **On** and click **Save**.

When you complete the integration steps on both portals, you'll be able to see relevant alerts in the machine details or user details page.

## Office 365 Threat Intelligence connection
This feature is only available if you have an active Office 365 E5 or the Threat Intelligence add-on. For more information, see the Office 365 Enterprise E5 product page.

When you enable this feature, you'll be able to incorporate data from Office 365 Advanced Threat Protection into Windows Defender Security Center to conduct a holistic security investigation across Office 365 mailboxes and Windows machines.

>[!NOTE]
>You'll need to have the appropriate license to enable this feature. 

To receive contextual machine integration in Office 365 Threat Intelligence, you'll need to enable the Windows Defender ATP settings in the Security & Compliance dashboard. For more information, see [Office 365 Threat Intelligence overview](https://support.office.com/en-us/article/Office-365-Threat-Intelligence-overview-32405DA5-BEE1-4A4B-82E5-8399DF94C512).

## Microsoft Cloud App Security
Enabling this setting forwards Windows Defender ATP signals to Microsoft Cloud App Security to provide deeper visibility into cloud application usage. Forwarded data is stored and processed in the same location as your Cloud App Security data. 

>[!NOTE]
>This feature is available with an E5 license for [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) on machines running Windows 10 version 1809 or later.

## Azure Information Protection
Turning this setting on forwards signals to Azure Information Protection, giving data owners and administrators visibility into protected data on onboarded machines and machine risk ratings.


## Microsoft Intune connection
This feature is only available if you have an active Microsoft Intune (Intune) license. 

When you enable this feature, you'll be able to share Windows Defender ATP device information to Intune and enhance policy enforcement. 

>[!NOTE]
>You'll need to enable the integration on both Intune and Windows Defender ATP to use this feature. 


## Preview features
Learn about new features in the Windows Defender ATP preview release and be among the first to try upcoming features by turning on the preview experience.

You'll have access to upcoming features which you can provide feedback on to help improve the overall experience before features are generally available.

## Enable advanced features
1. In the navigation pane, select **Preferences setup** > **Advanced features**.
2. Select the advanced feature you want to configure and toggle the setting between **On** and **Off**.
3. Click **Save preferences**.

## Related topics
- [Update data retention settings](data-retention-settings-windows-defender-advanced-threat-protection.md)
- [Configure alert notifications](configure-email-notifications-windows-defender-advanced-threat-protection.md)
- [Enable and create Power BI reports using Windows Defender ATP data](powerbi-reports-windows-defender-advanced-threat-protection.md)
- [Enable Secure Score security controls](enable-secure-score-windows-defender-advanced-threat-protection.md)
