---
title: Review and approve remediation actions following automated investigations in the Microsoft Defender Security Center
description: Review and approve (or reject) remediation actions following an automated investigation.
keywords: autoir, automated, investigation, detection, dashboard, source, threat types, id, tags, devices, duration, filter export
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: 
- m365-security-compliance 
- m365initiative-defender-endpoint 
ms.topic: conceptual
ms.date: 09/15/2020
---

# Review and approve remediation actions following an automated investigation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


## Remediation actions

When an [automated investigation](automated-investigations.md) runs, a verdict is generated for each piece of evidence investigated. Verdicts can be *Malicious*, *Suspicious*, or *No threats found*. 

Depending on

- the type of threat, 
- the resulting verdict, and 
- how your organization's [device groups](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/machine-groups) are configured, 

remediation actions can occur automatically or only upon approval by your organization’s security operations team. 

Here are a few examples:

- Example 1: Fabrikam's device groups are set to **Full - remediate threats automatically** (this is the recommended setting). In this case, remediation actions are taken automatically for artifacts that are considered to be malicious following an automated investigation. (See [Review completed actions](#review-completed-actions).)

- Example 2: Contoso's devices are included in a device group that is set for **Semi - require approval for any remediation**. In this case, Contoso's security operations team must review and approve all remediation actions following an automated investigation. (See [Review pending actions](#review-pending-actions).)

- Example 3: Tailspin Toys has their device groups set to **No automated response** (this is not recommended). In this case, automated investigations do not occur. As a result, no remediation actions are taken or pending, and no actions are logged in the [Action center](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/auto-investigation-action-center#the-action-center) for their devices. (See [Manage device groups](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/machine-groups#manage-device-groups))

Whether taken automatically or upon approval, remediation actions following an automated investigation include the following:
- Quarantine a file
- Remove a registry key 
- Kill a process 
- Stop a service 
- Remove a registry key 
- Disable a driver 
- Remove a scheduled task

### Automated investigation results and remediation actions

The following table summarizes remediation actions following an automated investigation, how device group settings affect whether actions are taken automatically or upon approval, and what to do in each case. 

|Device group setting | Automated investigation results | What to do |
|:---|:---|:---|
|**Full - remediate threats automatically** (this is the recommended setting) |A verdict of *Malicious* is reached for a piece of evidence. <br/><br/>Appropriate remediation actions are taken automatically. |[Review completed actions](#review-completed-actions) |
|**Full - remediate threats automatically** |A verdict of *Suspicious* is reached for a piece of evidence. <br/><br/>Remediation actions are pending approval to proceed. | [Approve (or reject) pending actions](#review-pending-actions) |
|**Semi - require approval for any remediation**  |A verdict of either *Malicious* or *Suspicious* is reached for a piece of evidence. <br/><br/>Remediation actions are pending approval to proceed.  |[Approve (or reject) pending actions](#review-pending-actions) |
|**Semi - require approval for core folders remediation** |A verdict of *Malicious* is reached for a piece of evidence. <br/><br/>If the artifact is a file or executable and is in an operating system directory, such as the Windows folder or the Program files folder, then remediation actions are pending approval. <br/><br/>If the artifact is *not* in an operating system directory, remediation actions are taken automatically. |1. [Approve (or reject) pending actions](#review-pending-actions)<br/><br/>2. [Review completed actions](#review-completed-actions) |
|**Semi - require approval for core folders remediation** |A verdict of *Suspicious* is reached for a piece of evidence. <br/><br/>Remediation actions are pending approval.  |[Approve (or reject) pending actions](#review-pending-actions).|
|**Semi - require approval for non-temp folders remediation** |A verdict of *Malicious* is reached for a piece of evidence. <br/><br/>If the artifact is a file or executable that is not in a temporary folder, such as the user's downloads folder or temp folder, remediation actions are pending approval. <br/><br/>If the artifact is a file or executable that *is* in a temporary folder, remediation actions are taken automatically.  |1. [Approve (or reject) pending actions](#review-pending-actions)<br/><br/>2. [Review completed actions](#review-completed-actions)  |
|**Semi - require approval for non-temp folders remediation** |A verdict of *Suspicious* is reached for a piece of evidence. <br/><br/>Remediation actions are pending approval. |[Approve (or reject) pending actions](#review-pending-actions)  | 
|Any of the **Full** or **Semi** automation levels |A verdict of *No threats found* is reached for a piece of evidence. <br/><br/>No remediation actions are taken, and no actions are pending approval. |[View details and results of automated investigations](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/auto-investigation-action-center) |
|**No automated response** (this is not recommended)|No automated investigations run, so no verdicts are reached, and no remediation actions are taken or awaiting approval. |[Consider setting up or changing your device groups to use **Full** or **Semi** automation](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/machine-groups) |

In Microsoft Defender for Endpoint, all verdicts are [tracked and viewable in the Microsoft Defender Security Center](#review-completed-actions).

> [!TIP]
> To learn more about remediation actions following an automated investigation, see [How threats are remediated](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated). 


## Review pending actions

1. Go to the Microsoft Defender Security Center ([https://securitycenter.windows.com](https://securitycenter.windows.com)) and sign in. You'll see the [Security operations dashboard](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard).

2. On the Security operations dashboard, in the navigation pane on the left, choose **Automated investigations** > **Action center**.

3. Review any items on the **Pending** tab. 

4. Select an investigation from any of the categories to open a panel where you can approve or reject remediation actions. 

   Other details such as file or service details, investigation details, and alert details are displayed. From the panel, you can click on the **Open investigation page** link to see the investigation details. You can also select multiple investigations to approve or reject actions on multiple investigations. 

## Review completed actions

1. Go to the Microsoft Defender Security Center ([https://securitycenter.windows.com](https://securitycenter.windows.com)) and sign in. You'll see the [Security operations dashboard](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard).

2. On the Security operations dashboard, in the navigation pane on the left, choose **Automated investigations** > **Action center**.

3. Select the **History** tab. (If need be, expand the time period to display more data.)

4. Select an item to view more details about that remediation action.
 
## Next steps

- [See the interactive guide: Investigate and remediate threats with Microsoft Defender ATP](https://aka.ms/MDATP-IR-Interactive-Guide)

- [View details and results of automated investigations](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/auto-investigation-action-center)

