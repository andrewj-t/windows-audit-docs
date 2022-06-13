---
title: Deploying Windows Defender Application Control AppId Tagging policies (Windows)
description: How to deploy your WDAC AppId Tagging policies locally and globally within your managed environment
keywords: security, malware
ms.assetid: 8d6e0474-c475-411b-b095-1c61adb2bdbb
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.collection: M365-security-compliance
author: jgeurten
ms.reviewer: jsuther1974
ms.author: dansimp
manager: dansimp
ms.date: 04/29/2022
ms.technology: windows-sec
---

# Deploying Windows Defender Application Control AppId Tagging policies (Windows)

**Applies to:**

-   Windows 10
-   Windows 11
-   Windows Server 2016 and above

> [!NOTE]
> Some capabilities of Windows Defender Application Control are only available on specific Windows versions. Learn more about the [Windows Defender Application Control feature availability](../feature-availability.md).

Similar to Windows Defender Application Control (WDAC) policies, WDAC AppId Tagging policies can be deployed locally and to your managed endpoints several ways. Once you've created your AppId Tagging policy, use one of the following methods to deploy:

1. [Deploy AppId Tagging Policies with MDM](#deploy-appid-tagging-policies-with-mdm)
1. [Deploy policies with MEMCM](#deploy-appid-tagging-policies-with-memcm)
1. [Deploy policies using scripting](#deploy-appid-tagging-policies-via-scripting)
1. [Deploy using the ApplicationControl CSP](#deploying-policies-via-the-applicationcontrol-csp)

## Deploy AppId Tagging Policies with MDM

Custom AppId Tagging policies can be deployed to endpoints using [the OMA-URI feature in MDM](../deploy-windows-defender-application-control-policies-using-intune.md#deploy-wdac-policies-with-custom-oma-uri). 

## Deploy AppId Tagging Policies with MEMCM

Custom AppId Tagging policies can deployed via MEMCM using the [deployment task sequences](/deployment/deploy-windows-defender-application-control-policies-with-memcm.md#deploy-custom-wdac-policies-using-packagesprograms-or-task-sequences), policies can be deployed to your managed endpoints and users. 

### Deploy AppId Tagging Policies via Scripting

Scripting hosts can be used to deploy AppId Tagging policies as well. This approach is often best suited for local deployment, but works for deployment to managed endpoints and users too. The [Deploy Windows Defender Application Control policies using script article](/deployment/deploy-wdac-policies-with-script.md) describes how to deploy WDAC AppId Tagging policies via scripting. Only the method for deploying to version 1903 and above is applicable for AppId Tagging policies. 

### Deploying policies via the ApplicationControl CSP

Multiple WDAC policies can be managed from an MDM server through ApplicationControl configuration service provider (CSP). The CSP also provides support for rebootless policy deployment.

However, when policies are unenrolled from an MDM server, the CSP will attempt to remove every policy from devices, not just the policies added by the CSP. The reason for this is that the ApplicationControl CSP doesn't track enrollment sources for individual policies, even though it will query all policies on a device, regardless if they were deployed by the CSP.

For more information, see [ApplicationControl CSP](/windows/client-management/mdm/applicationcontrol-csp) to deploy multiple policies, and optionally use MEM Intune's Custom OMA-URI capability.

> [!NOTE]
> WMI and GP do not currently support multiple policies. Instead, customers who can't directly access the MDM stack should use the [ApplicationControl CSP via the MDM Bridge WMI Provider](/windows/client-management/mdm/applicationcontrol-csp#powershell-and-wmi-bridge-usage-guidance) to manage Multiple Policy Format Windows Defender Application Control policies.
