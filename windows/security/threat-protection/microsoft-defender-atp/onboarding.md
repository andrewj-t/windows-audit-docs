---
title: Onboard to the Microsoft Defender ATP service
description: Learn how to onboard endpoints to Microsoft Defender ATP service
keywords: 
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: 
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario  
ms.topic: article
---

# Onboard to the Microsoft Defender ATP service

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**
- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)](https://go.microsoft.com/fwlink/p/?linkid=2146631)


Deploying Microsoft Defender ATP is a three-phase process:

| [![deployment phase - prepare](/windows/media/phase-diagrams/prepare.png)](prepare-deployment.md)<br>[Phase 1: Prepare](prepare-deployment.md) | [![deployment phase - setup](/windows/media/phase-diagrams/setup.png)](production-deployment.md)<br>[Phase 2: Setup](production-deployment.md) | ![deployment phase - onboard](/windows/media/phase-diagrams/onboard.png)<br>Phase 3: Onboard |
| ----- | ----- | ----- |
| | |*You are here!*|

You are currently in the onboarding phase.

These are the steps you need to take to deploy Microsoft Defender ATP:

- Step 1: Onboard endpoints to the service 
- Step 2: Configure capabilities 

## Step 1: Onboard endpoints using any of the supported management tools
The [Plan deployment](deployment-strategy.md) topic outlines the general steps you need to take to deploy Microsoft Defender ATP.  

After identifying your architecture, you'll need to decide which deployment method to use. The deployment tool you choose influences how you onboard endpoints to the service. 

### Onboarding tool options

The following table lists the available tools based on the endpoint that you need to onboard.

| Endpoint     | Tool options                       |
|--------------|------------------------------------------|
| **Windows**  |  [Local script (up to 10 devices)](configure-endpoints-script.md) <br>  [Group Policy](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobile Device Manager](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [VDI scripts](configure-endpoints-vdi.md)   |
| **macOS**    | [Local scripts](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Mobile Device Management](mac-install-with-other-mdm.md) |
| **Linux Server** | [Local script](linux-install-manually.md) <br> [Puppet](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [App-based](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 


## Step 2: Configure capabilities
After onboarding the endpoints, you'll then configure the various capabilities such as endpoint detection and response, next-generation protection, and attack surface reduction. 


## Example deployments
In this deployment guide, we'll guide you through using two deployment tools to onboard endpoints and how to configure capabilities.

The tools in the example deployments are:
- [Onboarding using Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Onboarding using Microsoft Endpoint Manager](onboarding-endpoint-manager.md)

Using the mentioned deployment tools above, you'll then be guided in configuring the following Microsoft Defender ATP capabilities:
- Endpoint detection and response configuration
- Next-generation protection configuration
- Attack surface reduction configuration

## Related topics
- [Onboarding using Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Onboarding using Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
