---
title: Planning Domain Isolation Zones (Windows)
description: Learn how to use information you've gathered to make decisions about isolation zones for your environment in Windows Defender Firewall with Advanced Security.
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

# Planning Domain Isolation Zones

**Applies to**
-   Windows 10
-   Windows 11
-   Windows Server 2016 and above

After you have the required information about your network, Active Directory, and client and server devices, you can use that information to make decisions about the isolation zones you want to use in your environment.

The bulk of the work in planning server and domain isolation is determining which devices to assign to each isolation zone. Correctly choosing the zone for each device is important to providing the correct level of security without compromising performance or the ability for a device to send or receive required network traffic.

The zones described in this guide include:

-   [Exemption List](exemption-list.md)

-   [Isolated Domain](isolated-domain.md)

-   [Boundary Zone](boundary-zone.md)

-   [Encryption Zone](encryption-zone.md)
