---
title: Is domain seen in org API
description: Use this API to create calls related to checking whether a domain was seen in the organization.
keywords: apis, graph api, supported apis, domain, domain seen
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
ms.date: 04/24/2018
---

# Was domain seen in org

[!include[Prerelease�information](prerelease.md)]

**Applies to:**

- Windows Defender Advanced Threat Protection (Windows Defender ATP)

Answers whether a domain was seen in the organization. 

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Create your app](exposed-apis-windows-defender-advanced-threat-protection-new.md#create-an-app)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	Url.Read.All |	'Read URLs'

## HTTP request
```
GET /api/domains/{domain}
```

## Request headers

Header | Value 
:---|:---
Authorization | Bearer {token}. **Required**.


## Request body
Empty

## Response
If successful and domain exists - 200 OK. If domain does not exist - 404 Not Found.

## Example

**Request**

Here is an example of the request.

[!include[Improve request performance](improverequestperformance-new.md)]

```
GET https://api.securitycenter.windows.com/api/domains/example.com
Content-type: application/json
```

**Response**

Here is an example of the response.


```
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.windows.com/api/$metadata#Domains/$entity",
    "host": "example.com"
}
```
