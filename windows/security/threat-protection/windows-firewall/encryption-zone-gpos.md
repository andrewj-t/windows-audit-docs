---
title: Encryption Zone GPOs (Windows)
description: Learn how to add a device to an encryption zone by adding the device account to the encryption zone group in Windows Defender Firewall with Advanced Security.
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

# Encryption Zone GPOs

**Applies to**
-   Windows 10
-   Windows 11
-   Windows Server 2016 and above

Handle encryption zones in a similar manner to the boundary zones. A device is added to an encryption zone by adding the device account to the encryption zone group. Woodgrove Bank has a single service that must be protected, and the devices that are running that service are added to the group CG\_DOMISO\_Encryption. This group is granted Read and Apply Group Policy permissions in on the GPO described in this section.

The GPO is only for server versions of Windows. Client devices aren't expected to participate in the encryption zone. If the need for one occurs, either create a new GPO for that version of Windows or expand the WMI filter attached to one of the existing encryption zone GPOs to make it apply to the client version of Windows.

-   [GPO\_DOMISO\_Encryption](gpo-domiso-encryption.md)
