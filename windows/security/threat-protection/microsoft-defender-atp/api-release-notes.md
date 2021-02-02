---
title: Microsoft Defender for Endpoint API release notes
description: Release notes for updates made to the Microsoft Defender for Endpoint set of APIs.
keywords: microsoft defender for endpoint api release notes, mde, apis, mdatp api, updates, notes, release
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.technology: mde
---

# Microsoft Defender for Endpoint API release notes

**Applies to:** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)

- Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

The following information lists the updates made to the Microsoft Defender for Endpoint APIs and the dates they were made.


### 25.01.2021
<hr>

- Updated rate limitations for [Advanced Hunting API](run-advanced-query-api.md) from 15 to 45 requests per minute. 

<br>

### 21.01.2021
<hr>

- Added new API: [Find devices by tag](machine-tags.md). 
- Added new API: [Import Indicators](import-ti-indicators.md). 

<br>

### 03.01.2021
<hr>

- Updated Alert evidence: added ***detectionStatus***, ***parentProcessFilePath*** and ***parentProcessFileName*** properties.
- Updated [Alert entity](alerts.md): added ***detectorId*** property.

<br>

### 15.12.2020
<hr>

- Updated [Device](machine.md) entity: added ***IpInterfaces*** list. See [List devices](get-machines.md).

<br>

### 04.11.2020
<hr>

- Added new API: [Set device value](set-device-value.md).
- Updated [Device](machine.md) entity: added ***deviceValue*** property.

<br>

### 01.09.2020
<hr>

- Added option to expand the Alert entity with its related Evidence. See [List Alerts](get-alerts.md).

<br>
<br>