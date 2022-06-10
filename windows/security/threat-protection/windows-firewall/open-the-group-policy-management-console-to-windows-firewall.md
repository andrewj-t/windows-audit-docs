---
title: Group Policy Management of Windows Defender Firewall (Windows)
description: Group Policy Management of Windows Defender Firewall with Advanced Security
ms.reviewer: 
ms.author: dansimp
ms.prod: m365-security
ms.localizationpriority: medium
author: dansimp
manager: dansimp
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.date: 09/08/2021
ms.technology: windows-sec
---

# Group Policy Management of Windows Defender Firewall

**Applies to**
-   Windows 10
-   Windows 11
-   Windows Server 2016 and above

To open a GPO to Windows Defender Firewall:

1.  Open the Group Policy Management console.

2.  In the navigation pane, expand **Forest:** *YourForestName*, expand **Domains**, expand *YourDomainName*, expand **Group Policy Objects**, right-click the GPO you want to modify, and then click **Edit**.

3.  In the navigation pane of the Group Policy Object Editor, navigate to **Computer Configuration** > **Administrative Templates** > **Network** > **Network Connections** > **Windows Defender Firewall**.
