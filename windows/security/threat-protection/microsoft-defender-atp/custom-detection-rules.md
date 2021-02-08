---
title: Create custom detection rules in Microsoft Defender ATP
ms.reviewer: 
description: Learn how to create custom detection rules based on advanced hunting queries
keywords: custom detections, create, manage, alerts, edit, run on demand, frequency, interval, detection rules, advanced hunting, hunt, query, response actions, mdatp, microsoft defender atp
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 09/20/2020
ms.technology: mde
---

# Create custom detection rules

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Applies to:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)

Custom detection rules built from [advanced hunting](advanced-hunting-overview.md) queries let you proactively monitor various events and system states, including suspected breach activity and misconfigured devices. You can set them to run at regular intervals, generating alerts and taking response actions whenever there are matches.

Read this article to learn how to create new custom detection rules. Or [see viewing and managing existing rules](custom-detections-manage.md).

> [!NOTE]
> To create or manage custom detections, [your role](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group) needs to have the **manage security settings** permission.

## 1. Prepare the query.

In Microsoft Defender Security Center, go to **Advanced hunting** and select an existing query or create a new query. When using a new query, run the query to identify errors and understand possible results.

>[!IMPORTANT]
>To prevent the service from returning too many alerts, each rule is limited to generating only 100 alerts whenever it runs. Before creating a rule, tweak your query to avoid alerting for normal, day-to-day activity.

### Required columns in the query results

To use a query for a custom detection rule, the query must return the following columns:

- `Timestamp`
- `DeviceId`
- `ReportId`

Simple queries, such as those that don't use the `project` or `summarize` operator to customize or aggregate results, typically return these common columns.

There are various ways to ensure more complex queries return these columns. For example, if you prefer to aggregate and count by `DeviceId`, you can still return `Timestamp` and `ReportId` by getting them from the most recent event involving each device.

The sample query below counts the number of unique devices (`DeviceId`) with antivirus detections and uses this to find only those devices with more than five detections. To return the latest `Timestamp` and the corresponding `ReportId`, it uses the `summarize` operator with the `arg_max` function.

```kusto
DeviceEvents
| where Timestamp > ago(7d)
| where ActionType == "AntivirusDetection"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| where count_ > 5
```

> [!TIP]
> For better query performance, set a time filter that matches your intended run frequency for the rule. Since the least frequent run is every 24 hours, filtering for the past day will cover all new data.

## 2. Create a new rule and provide alert details.

With the query in the query editor, select **Create detection rule** and specify the following alert details:

- **Detection name**—name of the detection rule
- **Frequency**—interval for running the query and taking action. [See additional guidance below](#rule-frequency)
- **Alert title**—title displayed with alerts triggered by the rule
- **Severity**—potential risk of the component or activity identified by the rule. [Read about alert severities](alerts-queue.md#severity)
- **Category**—type of threat component or activity, if any. [Read about alert categories](alerts-queue.md#understanding-alert-categories)
- **MITRE ATT&CK techniques**—one or more attack techniques identified by the rule as documented in the MITRE ATT&CK framework. This section is not available with certain alert categories, such as malware, ransomware, suspicious activity, and unwanted software
- **Description**—more information about the component or activity identified by the rule 
- **Recommended actions**—additional actions that responders might take in response to an alert

For more information about how alert details are displayed, [read about the alert queue](alerts-queue.md).

### Rule frequency

When saved, a new custom detection rule immediately runs and checks for matches from the past 30 days of data. The rule then runs again at fixed intervals and lookback durations based on the frequency you choose:

- **Every 24 hours**—runs every 24 hours, checking data from the past 30 days
- **Every 12 hours**—runs every 12 hours, checking data from the past 24 hours
- **Every 3 hours**—runs every 3 hours, checking data from the past 6 hours
- **Every hour**—runs hourly, checking data from the past 2 hours

> [!TIP]
> Match the time filters in your query with the lookback duration. Results outside of the lookback duration are ignored.

Select the frequency that matches how closely you want to monitor detections, and consider your organization's capacity to respond to the alerts.

## 3. Choose the impacted entities.

Identify the columns in your query results where you expect to find the main affected or impacted entity. For example, a query might return both device and user IDs. Identifying which of these columns represent the main impacted entity helps the service aggregate relevant alerts, correlate incidents, and target response actions.

You can select only one column for each entity type. Columns that are not returned by your query can't be selected.

## 4. Specify actions.

Your custom detection rule can automatically take actions on files or devices that are returned by the query.

### Actions on devices

These actions are applied to devices in the `DeviceId` column of the query results:

- **Isolate device**—applies full network isolation, preventing the device from connecting to any application or service, except for the Defender for Endpoint service. [Learn more about device isolation](respond-machine-alerts.md#isolate-devices-from-the-network)
- **Collect investigation package**—collects device information in a ZIP file. [Learn more about the investigation package](respond-machine-alerts.md#collect-investigation-package-from-devices)
- **Run antivirus scan**—performs a full Microsoft Defender Antivirus scan on the device
- **Initiate investigation**—starts an [automated investigation](automated-investigations.md) on the device
- **Restrict app execution**—sets restrictions on the device to allow only files that are signed with a Microsoft-issued certificate to run. [Learn more about restricting app execution](respond-machine-alerts.md#restrict-app-execution)

### Actions on files

These actions are applied to files in the `SHA1` or the `InitiatingProcessSHA1` column of the query results:

- **Allow/Block**—automatically adds the file to your [custom indicator list](manage-indicators.md) so that it is always allowed to run or blocked from running. You can set the scope of this action so that it is taken only on selected device groups. This scope is independent of the scope of the rule.
- **Quarantine file**—deletes the file from its current location and places a copy in quarantine

### Actions on users

- **Mark user as compromised**—sets the user's risk level to "high" in Azure Active Directory, triggering the corresponding [identity protection policies](https://docs.microsoft.com/azure/active-directory/identity-protection/overview-identity-protection#risk-levels).

## 5. Set the rule scope.

Set the scope to specify which devices are covered by the rule:

- All devices
- Specific device groups

Only data from devices in scope will be queried. Also, actions will be taken only on those devices.

## 6. Review and turn on the rule.

After reviewing the rule, select **Create** to save it. The custom detection rule immediately runs. It runs again based on configured frequency to check for matches, generate alerts, and take response actions.

You can [view and manage custom detection rules](custom-detections-manage.md), check their previous runs, and review the alerts they have triggered. You can also run a rule on demand and modify it.

## Related topics

- [View and manage custom detection rules](custom-detections-manage.md)
- [Custom detections overview](overview-custom-detections.md)
- [Advanced hunting overview](advanced-hunting-overview.md)
- [Learn the advanced hunting query language](advanced-hunting-query-language.md)
- [View and organize alerts](alerts-queue.md)
