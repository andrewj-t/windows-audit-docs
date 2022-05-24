---
title: Windows Defender Application Control Wizard
description: Microsoft Defender Application Control Wizard (WDAC) Wizard allows users to create, edit, and merge application control policies in a simple to use Windows application.
keywords: allowlisting, blocklisting, security, malware
ms.assetid: 8d6e0474-c475-411b-b095-1c61adb2bdbb
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.collection: M365-security-compliance
author: jgeurten
ms.reviewer: isbrahm
ms.author: dansimp
manager: dansimp
ms.topic: conceptual
ms.technology: windows-sec
---

# Windows Defender Application Control Wizard

**Applies to:**

- Windows 10
- Windows 11
- Windows Server 2016 and above

> [!NOTE]
> Some capabilities of Windows Defender Application Control are only available on specific Windows versions. Learn more about the [Windows Defender Application Control feature availability](feature-availability.md).

The Windows Defender Application Control (WDAC) policy wizard is an open-source Windows desktop application written in C# and bundled as an MSIX package. The wizard was built to provide security architects with security, and system administrators with a more user-friendly means to create, edit, and merge WDAC policies. The wizard desktop application uses the [ConfigCI PowerShell Cmdlets](/powershell/module/configci) in the backend so the output policy of the wizard and PowerShell cmdlets is identical.

## Downloading the application

The WDAC wizard can be downloaded from the official [WDAC Wizard installer website](https://webapp-wdac-wizard.azurewebsites.net) as an MSIX packaged application. The wizard's source code is available as part of Microsoft's Open Source Software offerings on GitHub at the [WDAC Wizard Repo](https://github.com/MicrosoftDocs/WDAC-Toolkit).

**Supported Clients**

As the WDAC wizard uses the cmdlets in the background, the wizard is functional on clients only where the cmdlets are supported as outlined in [WDAC feature availability](feature-availability.md). Specifically, the tool will verify that the client meets one of the following requirements: 

-   Windows builds 1909+
-   For pre-1909 builds, the Enterprise SKU of Windows is installed

If neither requirement is satisfied, the wizard will throw an error as the cmdlets are not available.

## Resources to learn more

| Topic | Description |
| - | - |
| [Creating a new base policy](wdac-wizard-create-base-policy.md) | This article describes how to create a new base policy using one of the supplied policy templates. |
| [Creating a new supplemental policy](wdac-wizard-create-supplemental-policy.md) | This article describes the steps necessary to create a supplemental policy, from one of the supplied templates, for an existing base policy. |
| [Editing a base or supplemental policy](wdac-wizard-editing-policy.md) | This article demonstrates how to modify an existing policy and the wizard's editing capabilities. |
| [Merging policies](wdac-wizard-merging-policies.md) | This article describes how to merge policies into a single application control policy. |
