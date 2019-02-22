---
title: Custom detections overview
description: Understand how how you can leverage the power of advanced hunting to create custom detections
keywords: custom detections, detections, advanced hunting, hunt, detect, query
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
ms.date: 10/29/2018
---


# Custom detections overview
**Applies to:**
- [Windows Defender Advanced Threat Protection (Windows Defender ATP)](https://wincom.blob.core.windows.net/documents/Windows10_Commercial_Comparison.pdf)


Alerts in Windows Defender ATP are surfaced through the system based on signals gathered from endpoints. With custom detections, you can create custom queries to monitor events for any kind of behavior such as suspicious or emerging threats.

This can be done by leveraging the power of Advanced hunting through the creation of custom detection rules. 
Custom detections are queries that run periodically every 24 hours and can be configured so that when the query meets the criteria you set, alerts are created and are surfaced in Windows Defender Security Center. These alerts will be treated like any other alert in the system.

This capability is particularly useful for scenarios when you want to pro-actively prevent threats and be notified quickly of emerging threats.

## Related topic
- [Create custom detection rules](custom-detection-rules.md)


