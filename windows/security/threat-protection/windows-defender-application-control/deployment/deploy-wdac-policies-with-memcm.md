---
title: Deploy Windows Defender Application Control (WDAC) policies by using Microsoft Endpoint Configuration Manager (MEMCM) (Windows)
description: You can use Microsoft Endpoint Configuration Manager (MEMCM) to configure Windows Defender Application Control (WDAC). Learn how with this step-by-step guide.
keywords: security, malware
ms.prod: m365-security
audience: ITPro
ms.collection: M365-security-compliance
author: jsuther1974
ms.reviewer: jogeurte
ms.author: jogeurte
ms.manager: jsuther
manager: dansimp
ms.date: 07/19/2021
ms.technology: windows-sec
ms.topic: article
ms.localizationpriority: medium
---

# Deploy WDAC policies by using Microsoft Endpoint Configuration Manager (MEMCM)

**Applies to:**

- Windows 10
- Windows 11
- Windows Server 2016 and above

>[!NOTE]
>Some capabilities of Windows Defender Application Control (WDAC) are only available on specific Windows versions. Learn more about the [Application Control feature availability](/windows/security/threat-protection/windows-defender-application-control/feature-availability).

You can use Microsoft Endpoint Configuration Manager (MEMCM) to configure Windows Defender Application Control (WDAC) on client machines.

## Use MEMCM's built-in policies

Configuration Manager includes native support for WDAC, which allows you to configure Windows 10 and Windows 11 client computers with a policy that will only allow:

- Windows components
- Microsoft Store apps
- Apps installed by Configuration Manager (Configuration Manager self-configured as a managed installer)
- [Optional] Reputable apps as defined by the Intelligent Security Graph (ISG)
- [Optional] Apps and executables already installed in admin-definable folder locations that Configuration Manager will allow through a one-time scan during policy creation on managed endpoints.

Note that Configuration Manager does not remove policies once deployed. To stop enforcement, you should switch the policy to audit mode, which will produce the same effect. If you want to disable Windows Defender Application Control (WDAC) altogether (including audit mode), you can deploy a script to delete the policy file from disk, and either trigger a reboot or wait for the next reboot.

For more information on using Configuration Manager's native WDAC policies, see [Windows Defender Application Control management with Configuration Manager](/mem/configmgr/protect/deploy-use/use-device-guard-with-configuration-manager).

## Deploy custom WDAC policies using Packages/Programs or Task Sequences

Using Configuration Manager's built-in policies can be a helpful starting point, but customers may find the circle-of-trust options available in Configuration Manager too limiting. To define your own circle-of-trust, you can use Configuration Manager to deploy custom WDAC policies using [script-based deployment](deploy-wdac-policies-with-script.md) via Software Distribution Packages and Programs or Operating System Deployment Task Sequences.
