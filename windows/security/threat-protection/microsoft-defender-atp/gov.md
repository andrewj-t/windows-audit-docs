---
title: Microsoft Defender ATP for US Government GCC High customers 
description: Learn about the requirements and the available Microsoft Defender ATP capabilities for US Government CCC High customers
keywords: government, gcc, high, requirements, capabilities, defender, defender atp, mdatp
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
ms.topic: conceptual
---

# Microsoft Defender for Endpoint for US Government GCC High customers

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Want to experience Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 


Microsoft Defender for Endpoint for US Government Community Cloud High (GCC High) customers, built in the US Azure Government environment, uses the same underlying technologies as Defender for Endpoint in Azure Commercial.

This offering is currently available to US Office 365 GCC High customers and is based on the same prevention, detection, investigation, and remediation as the commercial version. However, there are some key differences in the availability of capabilities for this offering.


## Endpoint versions
The following OS versions are supported:

- Windows 10, version 1903 
- Windows 10, version 1809 (OS Build 17763.404 with [KB4490481](https://support.microsoft.com/help/4490481))
- Windows 10, version 1803 (OS Build 17134.799 with [KB4499183](https://support.microsoft.com/help/4499183))
- Windows 10, version 1709 (OS Build 16299.1182 with [KB4499147](https://support.microsoft.com/help/4499147)) 
- Windows Server, 2019 (with [KB4490481](https://support.microsoft.com/help/4490481))

>[!NOTE]
A patch must be deployed before device onboarding in order to configure Defender for Endpoint to the correct environment.

The following OS versions are supported via Azure Security Center:
- Windows Server 2008 R2 SP1
- Windows Server 2012 R2
- Windows Server 2016

The following OS versions are not supported:
- Windows Server 2008 R2 SP1 (standalone, not via ASC)
- Windows Server 2012 R2 (standalone, not via ASC)
- Windows Server 2016 (standalone, not via ASC)
- Windows Server, version 1803
- Windows 7 SP1 Enterprise
- Windows 7 SP1 Pro
- Windows 8 Pro
- Windows 8.1 Enterprise
- macOS
- Linux

The initial release of Defender for Endpoint will not have immediate parity with the commercial offering. While our goal is to deliver all commercial features and functionality to our US Government (GCC High) customers, there are some capabilities not yet available that we'd like to highlight. These are the known gaps as of August 2020:

## Threat Analytics
Not currently available.

## Threat & Vulnerability Management
Not currently available.


## Automated investigation and remediation
The following capabilities are not currently available:
- Response to Office 365 alerts 
- Live response 



## Management and APIs
The following capabilities are not currently available:

- Threat protection report
- Device health and compliance report
- Integration with third-party products


## Email notifications
Not currently available.


## Integrations
Integrations with the following Microsoft products are not currently available:
- Azure Advanced Threat Protection
- Azure Information Protection
- Defender for Office 365
- Microsoft Cloud App Security
- Skype for Business
- Microsoft Intune (sharing of device information and enhanced policy enforcement)

## Microsoft Threat Experts
Not currently available.

## Required connectivity settings
You'll need to ensure that traffic from the following are allowed:

Service location | DNS record
:---|:---
Common URLs for all locations (Global location) | ```crl.microsoft.com```<br>```ctldl.windowsupdate.com```<br>```notify.windows.com```<br>```settings-win.data.microsoft.com``` <br><br> NOTE: ```settings-win.data.microsoft.com``` is only needed on Windows 10 devices running version 1803 or earlier.
Defender for Endpoint GCC High specific | ```us4-v20.events.data.microsoft.com``` <br>```winatp-gw-usgt.microsoft.com```<br>```winatp-gw-usgv.microsoft.com```<br>```*.blob.core.usgovcloudapi.net``` 



