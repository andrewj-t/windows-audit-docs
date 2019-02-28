---
title: Threat Protection (Windows 10)
description: Learn how Windows Defender ATP helps protect against threats.
keywords: threat protection, windows defender advanced threat protection, attack surface reduction, next generation protection, endpoint detection and response, automated investigation and response, secure score, advanced hunting
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.localizationpriority: medium
ms.date: 10/04/2018
---

# Threat Protection
[Windows Defender Advanced Threat Protection (Windows Defender ATP)](https://wincom.blob.core.windows.net/documents/Windows10_Commercial_Comparison.pdf) is a unified platform for preventative protection, post-breach detection, automated investigation, and response. Windows Defender ATP protects endpoints from cyber threats; detects advanced attacks and data breaches, automates security incidents and improves security posture.

<center><h2>Windows Defender ATP</center></h2>
<table>
<tr>
<td><a href="#asr"><center><img src="images/ASR_icon.png"> <br><b>Attack surface reduction</b></center></a></td>
<td><center><a href="#ngp"><img src="images/NGP_icon.png"><br> <b>Next generation protection</b></a></center></td>
<td><center><a href="#edr"><img src="images/EDR_icon.png"><br> <b>Endpoint detection and response</b></a></center></td>
<td><center><a href="#ai"><img src="images/AR_icon.png"><br> <b>Automated investigation and remediation</b></a></center></td>
<td><center><a href="#mte"><img src="images/MTE_icon.png"><br> <b>Microsoft Threat Experts</b></a></center></td>
<td><center><a href="#ss"><img src="images/SS_icon.png"><br><b>Secure score</b></a></center></td>
<td><center><img src="images/AH_icon.png"><a href="#ah"><br><b>Advanced hunting</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="#apis"><center><b>Management and APIs</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="#mtp"><center><b>Microsoft Threat Protection</a></center></b></td>
</tr>
</table>
<br>


<a name="asr"></a>

**[Attack surface reduction](windows-defender-atp/overview-attack-surface-reduction.md)**<br>
The attack surface reduction set of capabilities provide the first line of defense in the stack. By ensuring configuration settings are properly set and exploit mitigation techniques are applied, these set of capabilities resist attacks and exploitations. 

- [Hardware based isolation](windows-defender-atp/overview-hardware-based-isolation.md) 
- [Application control](windows-defender-application-control/windows-defender-application-control.md)
- [Device control](device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control.md)
- [Exploit protection](windows-defender-exploit-guard/exploit-protection-exploit-guard.md)
- [Network protection](windows-defender-exploit-guard/network-protection-exploit-guard.md)
- [Controlled folder access](windows-defender-exploit-guard/controlled-folders-exploit-guard.md)
- [Network firewall](windows-firewall/windows-firewall-with-advanced-security.md)
- [Attack surface reduction controls](windows-defender-exploit-guard/attack-surface-reduction-exploit-guard.md)

<a name="ngp"></a>

**[Next generation protection](windows-defender-antivirus/windows-defender-antivirus-in-windows-10.md)**<br>
To further reinforce the security perimeter of your network, Windows Defender ATP uses next generation protection designed to catch all types of emerging threats.

- [Behavior monitoring](/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus)
- [Cloud-based protection](/windows/security/threat-protection/windows-defender-antivirus/enable-cloud-protection-windows-defender-antivirus)
- [Machine learning](windows-defender-antivirus/utilize-microsoft-cloud-protection-windows-defender-antivirus.md)
- [URL Protection](/windows/security/threat-protection/windows-defender-antivirus/configure-network-connections-windows-defender-antivirus)
- [Automated sandbox service](windows-defender-antivirus/configure-block-at-first-sight-windows-defender-antivirus.md)

<a name="edr"></a>

**[Endpoint detection and response](windows-defender-atp/overview-endpoint-detection-response.md)**<br>
Endpoint detection and response capabilities are put in place to detect, investigate, and respond to advanced threats that may have made it past the first two security pillars. 

- [Alerts](windows-defender-atp/alerts-queue-windows-defender-advanced-threat-protection.md)
- [Historical endpoint data](windows-defender-atp/investigate-machines-windows-defender-advanced-threat-protection.md#machine-timeline)
- [Response orchestration](windows-defender-atp/response-actions-windows-defender-advanced-threat-protection.md)
- [Forensic collection](windows-defender-atp/respond-machine-alerts-windows-defender-advanced-threat-protection.md#collect-investigation-package-from-machines)
- [Threat intelligence](windows-defender-atp/threat-indicator-concepts-windows-defender-advanced-threat-protection.md)
- [Advanced detonation and analysis service](windows-defender-atp/respond-file-alerts-windows-defender-advanced-threat-protection.md#deep-analysis)

<a name="ai"></a>

**[Automated investigation and remediation](windows-defender-atp/automated-investigations-windows-defender-advanced-threat-protection.md)**<br>
In conjunction with being able to quickly respond to advanced attacks, Windows Defender ATP offers automatic investigation and remediation capabilities that help reduce the volume of alerts in minutes at scale. 

- [Automated investigation and remediation](windows-defender-atp/automated-investigations-windows-defender-advanced-threat-protection.md)
- [Threat remediation](windows-defender-atp/automated-investigations-windows-defender-advanced-threat-protection.md#how-threats-are-remediated)
- [Manage automated investigations](windows-defender-atp/manage-auto-investigation-windows-defender-advanced-threat-protection.md)
- [Analyze automated investigation](windows-defender-atp/manage-auto-investigation-windows-defender-advanced-threat-protection.md#analyze-automated-investigations)

<a name="mte"></a>

**[Microsoft Threat Experts](windows-defender-atp/microsoft-threat-experts.md)**<br>
In conjunction with being able to quickly respond to advanced attacks, Windows Defender ATP offers automatic investigation and remediation capabilities that help reduce the volume of alerts in minutes at scale. 

- [Targeted attack notification](windows-defender-atp/microsoft-threat-experts.md)
- [Experts-on-demand](windows-defender-atp/microsoft-threat-experts.md)
- [Configure your Microsoft Threat Protection managed hunting service](windows-defender-atp/configure-microsoft-threat-experts.md)


<a name="ss"></a>

**[Secure score](windows-defender-atp/overview-secure-score-windows-defender-advanced-threat-protection.md)**<br>
Windows Defender ATP includes a secure score to help you dynamically assess the security state of your enterprise network, identify unprotected systems, and take recommended actions to improve the overall security of your organization.
- [Asset inventory](windows-defender-atp/secure-score-dashboard-windows-defender-advanced-threat-protection.md)
- [Recommended improvement actions](windows-defender-atp/secure-score-dashboard-windows-defender-advanced-threat-protection.md)
- [Secure score](windows-defender-atp/overview-secure-score-windows-defender-advanced-threat-protection.md)
- [Threat analytics](windows-defender-atp/threat-analytics-dashboard-windows-defender-advanced-threat-protection.md)

<a name="ah"></a>

**[Advanced hunting](windows-defender-atp/overview-hunting-windows-defender-advanced-threat-protection.md)**<br>
Create custom threat intelligence and use a powerful search and query tool to hunt for possible threats in your organization.

- [Custom detection](windows-defender-atp/overview-custom-detections.md)
- [Realtime and historical hunting](windows-defender-atp/advanced-hunting-windows-defender-advanced-threat-protection.md)

<a name="apis"></a>

**[Management and APIs](windows-defender-atp/management-apis.md)**<br>
Integrate Windows Defender Advanced Threat Protection into your existing workflows.
- [Onboarding](windows-defender-atp/onboard-configure-windows-defender-advanced-threat-protection.md)
- [API and SIEM integration](windows-defender-atp/configure-siem-windows-defender-advanced-threat-protection.md)
- [Exposed APIs](windows-defender-atp/use-apis.md)
- [Role-based access control (RBAC)](windows-defender-atp/rbac-windows-defender-advanced-threat-protection.md)
- [Reporting and trends](windows-defender-atp/powerbi-reports-windows-defender-advanced-threat-protection.md)

<a name="mtp"></a>

**[Microsoft Threat Protection](windows-defender-atp/threat-protection-integration.md)** <br>
 Windows Defender ATP is part of the Microsoft Threat Protection solution that helps implement end-to-end security across possible attack surfaces in the modern workplace. Bring the power of Microsoft threat protection to your organization.
- [Conditional access](windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection.md)
- [O365 ATP](windows-defender-atp/threat-protection-integration.md)
- [Azure ATP](windows-defender-atp/threat-protection-integration.md)
- [Azure Security Center](windows-defender-atp/threat-protection-integration.md)
- [Skype for Business](windows-defender-atp/threat-protection-integration.md) 
- [Microsoft Cloud App Security](windows-defender-atp/microsoft-cloud-app-security-integration.md)













