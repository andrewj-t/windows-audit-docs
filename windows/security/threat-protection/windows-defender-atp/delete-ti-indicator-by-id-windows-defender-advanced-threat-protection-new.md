---
title: Delete Ti Indicator.
description: Deletes Ti Indicator entity by ID.
keywords: apis, public api, supported apis, delete, ti indicator, entity, id
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
ms.collection: M365-security-compliance 
ms.topic: article
ms.date: 12/08/2017
---

# Delete TI Indicator API

[!include[Prerelease�information](prerelease.md)]

>[!Note]
> Currently this API is supported only for AppOnly context requests. (See [Get access without a user](exposed-apis-create-app-webapp.md) for more information)


**Applies to:**

- Windows Defender Advanced Threat Protection (Windows Defender ATP)
Retrieves a TI Indicator entity by ID.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Windows Defender ATP APIs](apis-intro.md)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	Ti.ReadWrite |	'Read and write TI Indicators'


## HTTP request
```
Delete https://api.securitycenter.windows.com/api/tiindicators/{id}
```

[!include[Improve request performance](improverequestperformance-new.md)]


## Request headers

Name | Type | Description
:---|:---|:---
Authorization | String | Bearer {token}. **Required**.


## Request body
Empty

## Response
If TI Indicator exist and deleted successfully - 204 OK without content.
If TI Indicator with the specified id was not found - 404 Not Found.

## Example

**Request**

Here is an example of the request.

```
DELETE https://api.securitycenter.windows.com/api/tiindicators/220e7d15b0b3d7fac48f2bd61114db1022197f7f
```

**Response**

Here is an example of the response.


```
HTTP/1.1 204 NO CONTENT

```
