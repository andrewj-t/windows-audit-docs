---
title: Security recommendations by threat and vulnerability management
description: Get actionable security recommendations prioritized by threat, likelihood to be breached, and value, in threat and vulnerability management.
keywords: threat and vulnerability management, mdatp tvm security recommendation, cybersecurity recommendation, actionable security recommendation
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
# Security recommendations - threat and vulnerability management

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Threat and vulnerability management](next-gen-threat-and-vuln-mgt.md)

>Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

Cybersecurity weaknesses identified in your organization are mapped to actionable security recommendations and prioritized by their impact. Prioritized recommendations help shorten the time to mitigate or remediate vulnerabilities and drive compliance.

Each security recommendation includes actionable remediation steps. To help with task management, the recommendation can also be sent using Microsoft Intune and Microsoft Endpoint Configuration Manager. When the threat landscape changes, the recommendation also changes as it continuously collects information from your environment.

## How it works

Each device in the organization is scored based on three important factors to help customers to focus on the right things at the right time.

- **Threat** - Characteristics of the vulnerabilities and exploits in your organizations' devices and breach history. Based on these factors, the security recommendations show the corresponding links to active alerts, ongoing threat campaigns, and their corresponding threat analytic reports.

- **Breach likelihood** - Your organization's security posture and resilience against threats

- **Business value** - Your organization's assets, critical processes, and intellectual properties

## Navigate to the Security recommendations page

Access the Security recommendations page a few different ways:

- Threat and vulnerability management navigation menu in the [Microsoft Defender Security Center](portal-overview.md)
- Top security recommendations in the [threat and vulnerability management dashboard](tvm-dashboard-insights.md)

View related security recommendations in the following places:

- Software page
- Device page

### Navigation menu

Go to the threat and vulnerability management navigation menu and select **Security recommendations**. The page contains a list of security recommendations for the threats and vulnerabilities found in your organization.

### Top security recommendations in the threat and vulnerability management dashboard

In a given day as a Security Administrator, you can take a look at the [threat and vulnerability management dashboard](tvm-dashboard-insights.md) to see your [exposure score](tvm-exposure-score.md) side by side with your [Microsoft Secure Score for Devices](tvm-microsoft-secure-score-devices.md). The goal is to **lower** your organization's exposure from vulnerabilities, and **increase** your organization's device security to be more resilient against cybersecurity threat attacks. The top security recommendations list can help you achieve that goal.

![Example of Top security recommendations card, with four security recommendations.](images/top-security-recommendations350.png)

The top security recommendations list the improvement opportunities prioritized based on the important factors mentioned in the previous section - threat, likelihood to be breached, and value. Selecting a recommendation will take you to the security recommendations page with more details.

## Security recommendations overview

View recommendations, the number of weaknesses found, related components, threat insights, number of exposed devices, status, remediation type, remediation activities, impact to your exposure score and Microsoft Secure Score for Devices, and associated tags.

The color of the **Exposed devices** graph changes as the trend changes. If the number of exposed devices is on the rise, the color changes into red. If there's a decrease in the number of exposed devices, the color of the graph will change into green.

>[!NOTE]
>Threat and vulnerability management shows devices that were in use up to **30 days** ago. This is different from the rest of Microsoft Defender for Endpoint, where if a device has not been in use for more than 7 days it has in an ‘Inactive’ status.

![Example of the landing page for security recommendations.](images/tvmsecrec-updated.png)

### Icons

Useful icons also quickly call your attention to:
- ![arrow hitting a target](images/tvm_alert_icon.png) possible active alerts
- ![red bug](images/tvm_bug_icon.png) associated public exploits
- ![light bulb](images/tvm_insight_icon.png) recommendation insights

### Explore security recommendation options

Select the security recommendation that you want to investigate or process.

![Example of a security recommendation flyout page.](images/secrec-flyouteolsw.png)

From the flyout, you can choose any of the following options:

- **Open software page** - Open the software page to get more context on the software and how it's distributed. The information can include threat context, associated recommendations, weaknesses discovered, number of exposed devices, discovered vulnerabilities, names and detailed of devices with the software installed, and version distribution.

- [**Remediation options**](tvm-remediation.md) - Submit a remediation request to open a ticket in Microsoft Intune for your IT administrator to pick up and address. Track the remediation activity in the Remediation page.

- [**Exception options**](tvm-exception.md) - Submit an exception, provide justification, and set exception duration if you can't remediate the issue yet.

>[!NOTE]
>When a change is made on a device, it typically takes two hours for the data to be reflected in the Microsoft Defender Security Center. However, it may sometimes take longer.

### Investigate changes in device exposure or impact

If there is a large jump in the number of exposed devices, or a sharp increase in the impact on your organization exposure score and configuration score, then that security recommendation is worth investigating.

1. Select the recommendation and **Open software page**
2. Select the **Event timeline** tab to view all the impactful events related to that software, such as new vulnerabilities or new public exploits. [Learn more about event timeline](threat-and-vuln-mgt-event-timeline.md)
3. Decide how to address the increase or your organization's exposure, such as submitting a remediation request

## Request remediation

The threat and vulnerability management capability in Microsoft Defender ATP bridges the gap between Security and IT administrators through the remediation request workflow. Security admins like you can request for the IT Administrator to remediate a vulnerability from the **Security recommendation** pages to Intune.

### Enable Microsoft Intune connection

To use this capability, enable your Microsoft Intune connections. In the Microsoft Defender Security Center, navigate to **Settings** > **General** > **Advanced features**. Scroll down and look for **Microsoft Intune connection**. By default, the toggle is turned off. Turn your **Microsoft Intune connection** toggle **On**.

See [Use Intune to remediate vulnerabilities identified by Microsoft Defender ATP](https://docs.microsoft.com/intune/atp-manage-vulnerabilities) for details.

### Remediation request steps

1. Select a security recommendation you would like to request remediation for, and then select **Remediation options**.

2. Fill out the form, including what you are requesting remediation for, priority, due date, and optional notes. Select **Submit request**. Submitting a remediation request creates a remediation activity item within threat and vulnerability management, which can be used for monitoring the remediation progress for this recommendation. This will not trigger a remediation or apply any changes to devices.

3. Notify your IT Administrator about the new request and have them log into Intune to approve or reject the request and start a package deployment.

4. Go to the [**Remediation**](tvm-remediation.md) page to view the status of your remediation request.

If you want to check how the ticket shows up in Intune, see [Use Intune to remediate vulnerabilities identified by Microsoft Defender ATP](https://docs.microsoft.com/intune/atp-manage-vulnerabilities) for details.

>[!NOTE]
>If your request involves remediating more than 10,000 devices, we can only send 10,000 devices for remediation to Intune.

## File for exception

As an alternative to a remediation request when a recommendation is not relevant at the moment, you can create exceptions for recommendations. Only users with “exceptions handling” permissions can add exception. [Learn more about RBAC roles](user-roles.md). If your organization has device groups, you will now be able to scope the exception to specific device groups.

When an exception is created for a recommendation, the recommendation is no longer active. The recommendation state will change to **Full exception** or **Partial exception** (by device group).

### How to create an exception

Select a security recommendation you would like create an exception for, and then select **Exception options**.  

![Showing where the button for "exception options" is location in a security recommendation flyout.](images/tvm-exception-options.png)

Choose the scope and justification, set a date for the exception duration, and submit. To view all your exceptions (current and past), navigate to the [Remediation](tvm-remediation.md) page under the **Threat & Vulnerability Management** menu and select the **Exceptions** tab.

### Exception scope

Exceptions can either be created for selected device groups, or for all device groups past and present.  

#### Exception by device group

Apply the exception to all device groups or choose specific device groups. Device groups that already have an exception will not be displayed in the list. If you only select certain device groups, the recommendation state will change from “active” to “partial exception.” The state will change to “full exception” if you select all the device groups.

![Showing device group dropdown.](images/tvm-exception-device-group-500.png)

##### Filtered

If you have filtered by device group on any of the threat and vulnerability management pages, only your filtered device groups will appear as options.

Button to filter by device group on any of the threat and vulnerability management pages: 

![Showing selected device groups filter.](images/tvm-selected-device-groups.png)

Exception view with filtered device groups:

![Showing filtered device group dropdown.](images/tvm-exception-device-filter500.png)

##### Large number of device groups

If your organization has more than 20 device groups, select **Edit** next to the filtered device group option.

![Showing how to edit large numbers of groups.](images/tvm-exception-edit-groups.png)

A flyout will appear where you can search and choose device groups you want included. Select the check mark icon below Search to check/uncheck all.

![Showing large device group flyout.](images/tvm-exception-device-group-flyout-400.png)

#### Global exceptions

If you have global administrator permissions (called Microsoft Defender ATP administrator), you will be able to create and cancel a global exception. It affects **all** current and future device groups in your organization, and only a user with similar permission would be able to change it. The recommendation state will change from “active” to “full exception.”

![Showing global exception option.](images/tvm-exception-global.png)

Some things to keep in mind:

- If a recommendation is under global exception, then newly created exceptions for device groups will be suspended until the global exception has expired or been cancelled. After that point, the new device group exceptions will go into effect until they expire.
- If a recommendation already has exceptions for specific device groups and a global exception is created, then the device group exception will be suspended until it expires or the global exception is cancelled before it expires.

### Justification

Select your justification for the exception you need to file instead of remediating the security recommendation in question. Fill out the justification context, then set the exception duration.

The following list details the justifications behind the exception options:

- **Third party control** - A third party product or software already addresses this recommendation
        - Choosing this justification type will lower your exposure score and increase your secure score because your risk is reduced
- **Alternate mitigation** - An internal tool already addresses this recommendation
        - Choosing this justification type will lower your exposure score and increase your secure score because your risk is reduced
- **Risk accepted** - Poses low risk and/or implementing the recommendation is too expensive
- **Planned remediation (grace)** - Already planned but is awaiting execution or authorization

### View and cancel exceptions

Navigate to the **[Exceptions](tvm-exception.md)** tab in the **Remediation** page.

![Showing the "Exceptions" tab in the Remediation page.](images/tvm-exception-tab400.png)

Select an exception to open a flyout with more details. Exceptions per devices group will have a list of every device group the exception covers, which you can Export. You can also view the related recommendation or cancel the exception.

### View impact after exceptions are applied

In the Security Recommendations page, select **Customize columns** and check the boxes for **Exposed devices (after exceptions)** and **Impact (after exceptions)**.

![Showing customize columns options.](images/tvm-after-exceptions.png)

The exposed devices (after exceptions) column shows the remaining devices that are still exposed to vulnerabilities after exceptions are applied. Exception justifications that affect the exposure include ‘third party control’ and ‘alternate mitigation’. Other justifications do not reduce the exposure of a device, and they are still considered exposed.

The impact (after exceptions) shows remaining impact to exposure score or secure score after exceptions are applied. Exception justifications that affect the scores include ‘third party control’ and ‘alternate mitigation.’ Other justifications do not reduce the exposure of a device, and so the exposure score and secure score do not change.

![Showing the columns in the table.](images/tvm-after-exceptions-table.png)
If there is a large jump in the number of exposed devices, or a sharp increase in the impact on your organization exposure score and Microsoft Secure Score for Devices, then that security recommendation is worth investigating.

1. Select the recommendation and **Open software page**
2. Select the **Event timeline** tab to view all the impactful events related to that software, such as new vulnerabilities or new public exploits. [Learn more about event timeline](threat-and-vuln-mgt-event-timeline.md)
3. Decide how to address the increase or your organization's exposure, such as submitting a remediation request.

## Report inaccuracy

You can report a false positive when you see any vague, inaccurate, incomplete, or already remediated security recommendation information.

1. Open the Security recommendation.

2. Select the three dots beside the security recommendation that you want to report,  then select **Report inaccuracy**.

    ![Showing where the "Report inaccuracy" button is in a security recommendation flyout.](images/report-inaccuracy500.png)

3. From the flyout pane, select the inaccuracy category from the drop-down menu, fill in your email address, and details regarding the inaccuracy.

4. Select **Submit**. Your feedback is immediately sent to the threat and vulnerability management experts.

## Related articles

- [Threat and vulnerability management overview](next-gen-threat-and-vuln-mgt.md)
- [Dashboard](tvm-dashboard-insights.md)
- [Exposure score](tvm-exposure-score.md)
- [Microsoft Secure Score for Devices](tvm-microsoft-secure-score-devices.md)
- [Remediate vulnerabilities](tvm-remediation.md)
- [Create and view exceptions for security recommendations](tvm-exception.md)
- [Event timeline](threat-and-vuln-mgt-event-timeline.md)
