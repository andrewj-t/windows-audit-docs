---
title: Microsoft Defender ATP for Mac
ms.reviewer: 
description: Describes how to install and use Microsoft Defender ATP for Mac.
keywords: microsoft, defender, atp, mac, installation, deploy, uninstallation, intune, jamf, macos, mojave, high sierra, sierra
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance 
ms.topic: conceptual
---

# Microsoft Defender Advanced Threat Protection for Mac

This topic describes how to install, configure, update, and use Microsoft Defender ATP for Mac.

> [!CAUTION]
> Running other third-party endpoint protection products alongside Microsoft Defender ATP for Mac may lead to performance problems and unpredictable side effects.

## What’s new in the latest release

Since opening the public preview, we've been working non-stop to enhance the product, by listening to customer feedback. We've added management features and more granular controls for diagnostic data collection, refined the user experience, and fixed bugs.

If you have any feedback, please submit it to us by opening Microsoft Defender ATP for Mac on your device and navigating to **Help** > **Send feedback**.

## How to install Microsoft Defender ATP for Mac

### Prerequisites

- You must have a Microsoft Defender ATP subscription.
- You must have access to the Microsoft Defender Security Center portal.
- You should have beginner-level experience in macOS and BASH scripting. 
- If doing a manual deployment, you must have administrative privileges on the device.

### System requirements

> [!CAUTION]
> The three most recent released versions of macOS are supported. Beta versions of macOS are not supported.

- Supported macOS versions: 10.14 (Mojave), 10.13 (High Sierra), 10.12 (Sierra)
- Disk space: 650MB

After you've enabled the service, you may need to configure your network or firewall to allow outbound connections between it and your endpoints.

The following table lists the services and their associated URLs that your network must be able to connect to. You should ensure there are no firewall or network filtering rules that would deny access to these URLs, or you may need to create an *allow* rule specifically for them:

| Service        | Description                          | URL                                                                  |
| -------------- | ------------------------------------ | -------------------------------------------------------------------- |
| ATP            | Advanced threat protection service   | [https://x.cp.wd.microsoft.com](https://x.cp.wd.microsoft.com), [https://cdn.x.cp.wd.microsoft.com](https://cdn.x.cp.wd.microsoft.com) |

To test that a connection is not blocked, open [https://x.cp.wd.microsoft.com/api/report](https://x.cp.wd.microsoft.com/api/report) and [https://cdn.x.cp.wd.microsoft.com/ping]([https://cdn.x.cp.wd.microsoft.com/ping) in a browser.

If you prefer the command line, you can also check the connection by running the following command in Terminal:

```bash
curl -w ' %{url_effective}\n' 'https://x.cp.wd.microsoft.com/api/report' 'https://cdn.x.cp.wd.microsoft.com/ping'
```

The output from this command should look like this:

> `OK https://x.cp.wd.microsoft.com/api/report`
>
> `OK https://cdn.x.cp.wd.microsoft.com/ping`

> [!CAUTION]
> We recommend that you keep [System Integrity Protection](https://support.apple.com/en-us/HT204899) (SIP) enabled on client machines. SIP is a built-in macOS security feature that prevents low-level tampering with the OS, and is enabled by default.

### Installation instructions

There are several methods and deployment tools that you can use to install and configure Microsoft Defender ATP for Mac.

In general you'll need to take the following steps:

- Ensure you have a Microsoft Defender ATP subscription and have access to the Microsoft Defender ATP Portal
- Deploy Microsoft Defender ATP for Mac using one of the following deployment methods:
  - Via third party management tools:
    - [Microsoft Intune-based deployment](microsoft-defender-atp-mac-install-with-intune.md)
    - [JAMF-based deployment](microsoft-defender-atp-mac-install-with-jamf.md)
    - [Other MDM products](microsoft-defender-atp-mac-install-with-other-mdm.md)
  - Via the command line tool:
    - [Manual deployment](microsoft-defender-atp-mac-install-manually.md)

## How to update Microsoft Defender ATP for Mac

Microsoft regularly publishes software updates to improve performance, security, and to deliver new features. To update Microsoft Defender ATP for Mac, a program named Microsoft AutoUpdate (MAU) is used.

To read more on how to configure MAU in enterprise environments, refer to [Deploy updates for Microsoft Defender ATP for Mac](microsoft-defender-atp-mac-updates.md)

## How to configure Microsoft Defender ATP for Mac

Guidance for how to configure the product in enterprise environments is available in [Set preferences for Microsoft Defender ATP for Mac](microsoft-defender-atp-mac-preferences.md).

## Resources

- For additional information about logging, uninstalling, or known issues, see our [Resources](microsoft-defender-atp-mac-resources.md) page.

- [Privacy for Microsoft Defender ATP for Mac](microsoft-defender-atp-mac-privacy.md)
