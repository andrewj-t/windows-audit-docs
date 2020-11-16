---
title: Exposure score in threat and vulnerability management
description: The threat and vulnerability management exposure score reflects how vulnerable your organization is to cybersecurity threats.
keywords: exposure score, mdatp exposure score, mdatp tvm exposure score, organization exposure score, tvm organization exposure score, threat and vulnerability management, Microsoft Defender Advanced Threat Protection
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: ellevin
author: levinec
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: 
- m365-security-compliance 
- m365initiative-defender-endpoint  
ms.topic: conceptual
---
# Exposure score - threat and vulnerability management

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Threat and vulnerability management](next-gen-threat-and-vuln-mgt.md)

>Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

Your exposure score is visible in the [Threat and vulnerability management dashboard](tvm-dashboard-insights.md) of the Microsoft Defender Security Center. It reflects how vulnerable your organization is to cybersecurity threats. Low exposure score means your devices are less vulnerable from exploitation.

- Quickly understand and identify high-level takeaways about the state of security in your organization.
- Detect and respond to areas that require investigation or action to improve the current state.
- Communicate with peers and management about the impact of security efforts.

The card gives you a high-level view of your exposure score trend over time. Any spikes in the chart give you a visual indication of a high cybersecurity threat exposure that you can investigate further.

![Exposure score card](images/tvm_exp_score.png)

## How it works

The exposure score is broken down into the following levels:

- 0–29: low exposure score
- 30–69: medium exposure score
- 70–100: high exposure score

You can remediate the issues based on prioritized [security recommendations](tvm-security-recommendation.md) to reduce the exposure score. Each software has weaknesses that are transformed into recommendations and prioritized based on risk to the organization.

## How the score is calculated

The exposure score is continuously calculated on each device in the organization. It is scored & evaluated based on the following categories:

- **Threats** - external and internal threats such as public exploit code and security alerts
- **Likelihood** - likelihood of the device to get breached given its current security posture
- **Value** - value of the device to the organization given its role and content

**Device exposure score** = (Threats + Likelihood) x Value

**Organization exposure score** = Avg (All device exposure scores) taking into account organization value multipliers

### Threats

Points are added based on whether the device has any vulnerabilities or misconfigurations, determined by the Common Vulnerability Scoring System (CVSS) base score.

Further points are added based on:

- Exploits availability and whether the exploit is verified or ranked
- A threat campaign is linked to the vulnerability or misconfiguration

### Likelihood

Points are added based on whether any of the following factors are true:

- The device is internet facing
- Specific compensating controls are misconfigured
- An exploit attempt is linked directly to a threat spotted in the organization

### Value

Points are added based on whether any of the following factors are true for a device:

- Contains high business impact (HBI) data
- Marked as a High Value Asset (HVA) or serves as an important server role (e.g. AD, DNS)
- Runs a business critical app (BCA)
- Used by a marked high value user (HVU) (e.g. domain admin, CEO)

If a device is valuable to your organization, it should increase the total organization exposure score.

## Reduce your threat and vulnerability exposure

Lower your threat and vulnerability exposure by remediating [security recommendations](tvm-security-recommendation.md). Make the most impact to your exposure score by remediating the top security recommendations, which can be viewed in the [threat and vulnerability management dashboard](tvm-dashboard-insights.md).

## Related topics

- [Threat and vulnerability management overview](next-gen-threat-and-vuln-mgt.md)
- [Microsoft Secure Score for Devices](tvm-microsoft-secure-score-devices.md)
- [Security recommendations](tvm-security-recommendation.md)
- [Event timeline](threat-and-vuln-mgt-event-timeline.md)
