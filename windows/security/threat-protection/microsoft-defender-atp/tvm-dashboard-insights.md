---
title: What's in the dashboard and what it means for my organization's security posture
ms.reviewer: 
description: What's in the Threat & Vulnerability Management dashboard and how it can help SecOps and Security Administrators arrive at informed decisions in addressing cybersecurity threat vulnerabilities and building their organization's security resilience. 
keywords: mdatp-tvm, mdatp-tvm dashboard, threat & vulnerability management, risk-based threat & vulnerability management, security configuration, configuration score, exposure score    
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: eADQiWindows 10XVcnh
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: ellevin
author: levinec
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance 
ms.topic: conceptual
---
# Threat & Vulnerability Management dashboard overview

**Applies to:**
- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)](https://go.microsoft.com/fwlink/p/?linkid=2069559)

[!include[Prerelease information](prerelease.md)]

>Want to experience Microsoft Defender ATP? [Sign up for a free trial.](https://www.microsoft.com/en-us/WindowsForBusiness/windows-atp?ocid=docs-wdatp-portaloverview-abovefoldlink) 

Threat & Vulnerability Management is a component of Microsoft Defender ATP, and provides both security administrators and security operations teams with unique value, including:
- Real-time endpoint detection and response (EDR) insights correlated with endpoint vulnerabilities
- Invaluable machine vulnerability context during incident investigations
- Built-in remediation processes through Microsoft Intune and Microsoft System Center Configuration Manager (SCCM)  
  
   >[!NOTE]
   > Microsoft Intune and Microsoft System Center Configuration Manager (SCCM) integration will be available in the coming weeks.  

You can use the Threat & Vulnerability Management capability in [Microsoft Defender Security Center](https://securitycenter.windows.com/) to:
- View exposure and configuration scores side-by-side with top security recommendations, software vulnerability, remediation activities, and exposed machines
- Correlate EDR insights with endpoint vulnerabilities and process them 
- Select remediation options, triage and track the remediation tasks

## Threat & Vulnerability Management in Microsoft Defender Security Center
When you open the portal, you’ll see the main areas of the capability:

 ![Microsoft Defender Advanced Threat Protection portal](images/tvm_dashboard.png)
 
 ![Threat & Vulnerability Management menu](images/tvm_menu.png)

- (1) Menu in the navigation pane
- (2) Threat & Vulnerability Management icon
- (3) Threat & Vulnerability Management dashboard

You can navigate through the portal using the menu options available in all sections. Refer to the following table for a description of each section.

Area | Description
:---|:---
(1) Menu | Select menu to expand the navigation pane and see the names of the Threat & Vulnerability Management capabilities.
(2) Threat & Vulnerability Management navigation pane | Use the navigation pane to move across the **Threat and Vulnerability Management Dashboard**, **Security recommendations**, **Remediation**, and **Software inventory**. 
**Dashboards**	| Get a high-level view of the organization exposure score, MDATP configuration score, top remediation activities, top security recommendations, top vulnerable software, and top exposed machines data.
**Security recommendations** | See the list of security recommendations, their related components, insights, number or exposed devices, impact, and request for remediation. You can click each item on the list and it will open a flyout pane where you will see vulnerability details, and have the option to open the software page, and see the remediation options.
**Remediation** | See the remediation activity, related component, remediation type, status, due date, option to export the remediation and process data to CSV. 
**Software inventory** | See the list of applications, versions, weaknesses, whether there’s an exploit found on the application, prevalence in the organization, how many were installed, how many exposed devices are there, and the numerical value of the impact. You can select each item in the list and opt to open the software page which shows the vulnerabilities and misconfigurations associated and its machine and version distribution details.
(3) Threat & Vulnerability Management dashboard | Access the **Exposure score**, **Configuration score**, **Exposure distribution**, **Top security recommendations**, **Top vulnerable software**, **Top remediation activities**, **Top exposed machines**, and **Threat campaigns**.
**Organization Exposure score**	| See the current state of your organization’s device exposure to threats and vulnerabilities. Several factors affect your organization’s exposure score: weaknesses discovered in your devices, likelihood of your devices to be breached, value of the devices to your organization, and relevant alerts discovered with your devices. The goal is to lower down your organization’s exposure score to be more secure. To reduce the score, you need to remediate the related security configuration issues listed in the security recommendations. 
**MDATP Configuration score** | See the security posture of your organization’s operating system, applications, network, accounts and security controls. The goal is to increase your configuration score by remediating the related security configuration issues. You can click the bars and it will take you to the **Security recommendation** page for details.
**Machine exposure distribution** | See how many machines are exposed based on their exposure level. You can click the sections in the doughnut chart and it will take you to the **Machines list** page where you'll see the affected machine names, exposure level side by side with risk level, among other details such as domain, OS platform, its health state, when it was last seen, and its tags. 
**Top security recommendations** | See the collated security recommendations which are sorted and prioritized based on your organization’s risk exposure and the urgency that it requires. Useful icons also quickly calls your attention on possible active alerts ![possible active alert](images/tvm_alert_icon.png), associated public exploits ![threat insight](images/tvm_bug_icon.png), and recommendation insights ![recommendation insight](images/tvm_insight_icon.png). You can drill down on the security recommendation to see the potential risks, list of exposed machines, and read the insights. Thus, providing you with an informed decision to either proceed with a remediation request. Click **Show more** to see the rest of the security recommendations in the list.
**Top vulnerable software** | Get real-time visibility into the organizational software inventory, with stack-ranked list of vulnerable software installed on your network’s devices and how they impact on your organizational exposure score. Click each item for details or **Show more** to see the rest of the vulnerable application list in the **Software inventory** page.
**Top remediation activities** | Track the remediation activities generated from the security recommendations. You can click each item on the list to see the details in the **Remediation** page or click **Show more** to see the rest of the remediation activities.
**Top exposed machines** | See the exposed machine names and their exposure level. You can click each machine name from the list and it will take you to the machine page where you can view the alerts, risks, incidents, security recommendations, installed software, discovered vulnerabilities associated with the exposed machines. You can also do other EDR-related tasks in it, such as: manage tags, initiate automated investigations, initiate a live response session, collect an investigation package, run antivirus scan, restrict app execution, and isolate machine. You can also click **Show more** to see the rest of the exposed machines list.

See [Microsoft Defender ATP icons](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/portal-overview-windows-defender-advanced-threat-protection#windows-defender-atp-icons) for more information on the icons used throughout the portal.

## Related topics
- [Risk-based Threat & Vulnerability Management](next-gen-threat-and-vuln-mgt.md)
- [Configuration score](configuration-score.md)
- [Scenarios](threat-and-vuln-mgt-scenarios.md)
