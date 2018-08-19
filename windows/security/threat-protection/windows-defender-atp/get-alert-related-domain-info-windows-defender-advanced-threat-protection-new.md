---
title: Get alert related domains information 
description: Retrieves all domains related to a specific alert.
keywords: apis, graph api, supported apis, get alert information, alert information, related domain
search.product: eADQiWindows 10XVcnh
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
ms.date: 12/08/2017
---

# Get alert related domain information API

[!include[Prerelease�information](prerelease.md)]

**Applies to:**

- Windows Defender Advanced Threat Protection (Windows Defender ATP)


Retrieves all domains related to a specific alert.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Create your app](exposed-apis-windows-defender-advanced-threat-protection-new.md#create-an-app)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	URL.Read.All |	'Read URLs'

## HTTP request
```
GET /api/alerts/{id}/domains
```

## Request headers

Name | Type | Description
:---|:---|:---
Authorization | String | Bearer {token}. **Required**.


## Request body
Empty

## Response
If successful and alert and domain exist - 200 OK.
If alert not found or domain not found - 404 Not Found.


## Example

**Request**

Here is an example of the request.

[!include[Improve request performance](improverequestperformance-new.md)]


```
GET https://api.securitycenter.windows.com/alerts/636688558380765161_2136280442/domains
```

**Response**

Here is an example of the response.


```
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.windows.com/$metadata#Domains",
    "value": [
        {
            "host": "www.example.com"
        }
    ]
}

```
