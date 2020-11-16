---
title: Create and view exceptions for security recommendations - threat and vulnerability management
description: Create and monitor exceptions for security recommendations in threat and vulnerability management. 
keywords: microsoft defender atp tvm remediation, mdatp tvm, threat and vulnerability management, threat & vulnerability management, threat & vulnerability management remediation, tvm remediation intune, tvm remediation sccm
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
# Create and view exceptions for security recommendations - threat and vulnerability management

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Threat and vulnerability management](next-gen-threat-and-vuln-mgt.md)

>Want to experience Microsoft Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-portaloverview-abovefoldlink)

As an alternative to a remediation request when a recommendation is not relevant at the moment, you can create exceptions for recommendations. If your organization has device groups, you will now be able to scope the exception to specific device groups. Exceptions can either be created for selected device groups, or for all device groups past and present.  

When an exception is created for a recommendation, the recommendation is no longer active. The recommendation state will change to **Full exception** or **Partial exception** (by device group).

## Permissions

Only users with “exceptions handling” permissions can add exception. [Learn more about RBAC roles](user-roles.md).

## Create an exception

Select a security recommendation you would like create an exception for, and then select **Exception options** and fill out the form.  

![Showing where the button for "exception options" is location in a security recommendation flyout.](images/tvm-exception-options.png)

### Exception by device group

Apply the exception to all device groups or choose specific device groups. Device groups that already have an exception will not be displayed in the list. If you only select certain device groups, the recommendation state will change from “active” to “partial exception.” The state will change to “full exception” if you select all the device groups.

![Showing device group dropdown.](images/tvm-exception-device-group-500.png)

#### Filtered views

If you have filtered by device group on any of the threat and vulnerability management pages, only your filtered device groups will appear as options.

Button to filter by device group on any of the threat and vulnerability management pages: 

![Showing selected device groups filter.](images/tvm-selected-device-groups.png)

Exception view with filtered device groups:

![Showing filtered device group dropdown.](images/tvm-exception-device-filter500.png)

#### Large number of device groups

If your organization has more than 20 device groups, select **Edit** next to the filtered device group option.

![Showing how to edit large numbers of groups.](images/tvm-exception-edit-groups.png)

A flyout will appear where you can search and choose device groups you want included. Select the check mark icon below Search to check/uncheck all.

![Showing large device group flyout.](images/tvm-exception-device-group-flyout-400.png)

### Global exceptions

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

## View all exceptions

Navigate to the **Exceptions** tab in the **Remediation** page.

![Showing the "Exceptions" tab in the Remediation page.](images/tvm-exception-tab400.png)

Select an exception to open a flyout with more details. Exceptions per devices group will have a list of every device group the exception covers, which you can Export. You can also view the related recommendation or cancel the exception.

## How to cancel an exception

To cancel an exception, navigate to the **Exceptions** tab in the **Remediation** page. Select the exception.

### Cancel the exception for a specific device group

If the exception is per device group, then you will need to select the specific device group to cancel the exception for it. 

![Showing how to select a specific device group.](images/tvm-exception-device-group-hover.png)

A flyout will appear for the device group, and you can select **Cancel exception**.

### Cancel a global exception

If it is a global exception, select an exception from the list and then select **Cancel exception** from the flyout.

![Showing how to cancel the exception for a global exception.](images/tvm-exception-cancel-global-400.png)

## View impact after exceptions are applied

In the Security Recommendations page, select **Customize columns** and check the boxes for **Exposed devices (after exceptions)** and **Impact (after exceptions)**.

![Showing customize columns options.](images/tvm-after-exceptions.png)

The exposed devices (after exceptions) column shows the remaining devices that are still exposed to vulnerabilities after exceptions are applied. Exception justifications that affect the exposure include ‘third party control’ and ‘alternate mitigation’. Other justifications do not reduce the exposure of a device, and they are still considered exposed.

The impact (after exceptions) shows remaining impact to exposure score or secure score after exceptions are applied. Exception justifications that affect the scores include ‘third party control’ and ‘alternate mitigation.’ Other justifications do not reduce the exposure of a device, and so the exposure score and secure score do not change.

![Showing the columns in the table.](images/tvm-after-exceptions-table.png)
If there is a large jump in the number of exposed devices, or a sharp increase in the impact on your organization exposure score and Microsoft Secure Score for Devices, then that security recommendation is worth investigating.

1. Select the recommendation and **Open software page**
2. Select the **Event timeline** tab to view all the impactful events related to that software, such as new vulnerabilities or new public exploits. [Learn more about event timeline](threat-and-vuln-mgt-event-timeline.md)
3. Decide how to address the increase or your organization's exposure, such as submitting a remediation request.

## Related topics

- [Threat and vulnerability management overview](next-gen-threat-and-vuln-mgt.md)
- [Remediate vulnerabilities](tvm-remediation.md)
- [Security recommendations](tvm-security-recommendation.md)
- [Exposure score](tvm-exposure-score.md)
- [Microsoft Secure Score for Devices](tvm-microsoft-secure-score-devices.md)
