---
title: Check the health state of the sensor in Microsoft Defender ATP
description: Check the sensor health on devices to identify which ones are misconfigured, inactive, or are not reporting sensor data.
keywords: sensor, sensor health, misconfigured, inactive, no sensor data, sensor data, impaired communications, communication
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
ms.topic: article
ms.date: 04/24/2018
---

# Check sensor health state in Microsoft Defender ATP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Applies to:**
- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)](https://go.microsoft.com/fwlink/p/?linkid=2146631)

>Want to experience Microsoft Defender ATP? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-checksensor-abovefoldlink)

The **Devices with sensor issues** tile is found on the Security Operations dashboard. This tile provides information on the individual device’s ability to provide sensor data and communicate with the Microsoft Defender ATP service. It reports how many devices require attention and helps you identify problematic devices and take action to correct known issues.

There are two status indicators on the tile that provide information on the number of devices that are not reporting properly to the service:
- **Misconfigured** - These devices might partially be reporting sensor data to the Microsoft Defender ATP service and might have configuration errors that need to be corrected.
- **Inactive** - Devices that have stopped reporting to the Microsoft Defender ATP service for more than seven days in the past month.

Clicking any of the groups directs you to **Devices list**, filtered according to your choice.

![Screenshot of Devices with sensor issues tile](images/atp-devices-with-sensor-issues-tile.png)

On **Devices list**, you can filter the health state list by the following status:
- **Active** - Devices that are actively reporting to the Microsoft Defender ATP service.
- **Misconfigured** - These devices might partially be reporting sensor data to the Microsoft Defender ATP service but have configuration errors that need to be corrected. Misconfigured devices can have either one or a combination of the following issues:
  - **No sensor data** - Devices has stopped sending sensor data. Limited alerts can be triggered from the device.
  - **Impaired communications** - Ability to communicate with device is impaired. Sending files for deep analysis, blocking files, isolating device from network and other actions that require communication with the device may not work.
- **Inactive** - Devices that have stopped reporting to the Microsoft Defender ATP service.

You can also download the entire list in CSV format using the **Export** feature. For more information on filters, see [View and organize the Devices list](machines-view-overview.md).

>[!NOTE]
>Export the list in CSV format to display the unfiltered data. The CSV file will include all devices in the organization, regardless of any filtering applied in the view itself and can take a significant amount of time to download, depending on how large your organization is.

![Screenshot of Devices list page](images/atp-devices-list-page.png)

You can view the device details when you click on a misconfigured or inactive device.

## Related topic
- [Fix unhealthy sensors in Microsoft Defender ATP](fix-unhealthy-sensors.md)
