---
title: Use shared queries in advanced hunting
description: Start threat hunting immediately with predefined and shared queries. Share your queries to the public or to your organization.
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, microsoft defender atp, wdatp search, query, telemetry, custom detections, schema, kusto, github repo, my queries, shared queries
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
ms.technology: mde
---

# Use shared queries in advanced hunting

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Applies to:**
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2146631)

>Want to experience Defender for Endpoint? [Sign up for a free trial.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhunting-abovefoldlink)

[Advanced hunting](advanced-hunting-overview.md) queries can be shared among users in the same organization. You can also find queries shared publicly on GitHub. These queries let you quickly pursue specific threat hunting scenarios without having to write queries from scratch.

![Image of shared queries](images/atp-advanced-hunting-shared-queries.png)

## Save, modify, and share a query
You can save a new or existing query so that it is only accessible to you or shared with other users in your organization.

1. Type a new query or load an existing one from under **Shared queries** or **My queries**.

2. Select **Save** or **Save as** from the save options. To avoid overwriting an existing query, choose **Save as**.

3. Enter a name for the query.

   ![Image of saving a query](images/advanced-hunting-save-query.png)

4. Select the folder where you'd like to save the query.
    - **Shared queries** — shared to all users in your organization
    - **My queries** — accessible only to you
    
5. Select **Save**.

## Delete or rename a query
1. Right-click on a query you want to rename or delete.

    ![Image of delete query](images/atp_advanced_hunting_delete_rename.png)

2. Select **Delete** and confirm deletion. Or select **Rename** and provide a new name for the query.

## Create a direct link to a query
To generate a link that opens your query directly in the advanced hunting query editor, finalize your query and select **Share link**.

## Access queries in the GitHub repository  
Microsoft security researchers regularly share advanced hunting queries in a [designated public repository on GitHub](https://github.com/Microsoft/WindowsDefenderATP-Hunting-Queries). This repository is open to contributions. To contribute, [join GitHub for free](https://github.com/). 

>[!TIP]
>Microsoft security researchers also provide advanced hunting queries that you can use to locate activities and indicators associated with emerging threats. These queries are provided as part of the [threat analytics](threat-analytics.md) reports in Microsoft Defender Security Center.

## Related topics
- [Advanced hunting overview](advanced-hunting-overview.md)
- [Learn the query language](advanced-hunting-query-language.md)
- [Work with query results](advanced-hunting-query-results.md)
- [Understand the schema](advanced-hunting-schema-reference.md)
- [Apply query best practices](advanced-hunting-best-practices.md)
- [Custom detections overview](overview-custom-detections.md)
