---
title: Configure Threat & Vulnerability Management in Microsoft Defender ATP
ms.reviewer: 
description: Configure your Threat & Vulnerability Management to allow security administrators and IT administrators to collaborate seamlessly to remediate issues via Microsoft intune and Microsoft Endpoint Configuration Manager integrations.
keywords: RBAC, Threat & Vulnerability Management configuration, Threat & Vulnerability Management integrations, Microsft Intune integration with TVM, SCCM integration with TVM  
search.product: Windows 10
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
---
# Configure Threat & Vulnerability Management
**Applies to:**
- [Microsoft Defender Advanced Threat Protection Microsoft Defender ATP)](https://go.microsoft.com/fwlink/p/?linkid=2069559)

[!include[Prerelease information](../../includes/prerelease.md)]

This section guides you through the steps you need to take to configure Threat & Vulnerability Management's integration with Microsoft Intune or Microsoft Endpoint Configuration Manager for a seamless collaboration of issue remediation.

### Before you begin
> [!IMPORTANT]
> Threat & Vulnerability Management data currently supports Windows 10 devices. Upgrade to Windows 10 to account for the rest of your devices’ threat and vulnerability exposure data.</br>

Ensure that you have the right RBAC permissions to configure your Threat & Vulnerability Management integration with Microsoft Intune or Microsoft Endpoint Configuration Manager.   

>[!WARNING]
>Only Intune and Microsoft Endpoint Configuration Manager enrolled devices are supported in this scenario.</br>
>Use any of the following options to enroll devices in Intune:
>- IT Admin: For more information on how to enabling auto-enrollment, see [Windows Enrollment](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)
>- End-user: For more information on how to enroll your Windows 10 device in Intune, see [Enroll your Windows 10 device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-w10-device-access-work-or-school)
>- End-user alternative: For more information on joining an Azure AD domain, see [Set up Azure Active Directory joined devices](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup).

## Related topics

- [Threat & Vulnerability Management overview](next-gen-threat-and-vuln-mgt.md)
- [Supported operating systems and platforms](tvm-supported-os.md)
- [Threat & Vulnerability Management dashboard](tvm-dashboard-insights.md)
- [Exposure score](tvm-exposure-score.md)
- [Microsoft Secure Score for Devices](tvm-microsoft-secure-score-devices.md)
- [Security recommendations](tvm-security-recommendation.md)
- [Remediation and exception](tvm-remediation.md)
- [Software inventory](tvm-software-inventory.md)
- [Weaknesses](tvm-weaknesses.md)
- [Scenarios](threat-and-vuln-mgt-scenarios.md)
- [Configure data access for Threat & Vulnerability Management roles](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles#create-roles-and-assign-the-role-to-an-azure-active-directory-group)
