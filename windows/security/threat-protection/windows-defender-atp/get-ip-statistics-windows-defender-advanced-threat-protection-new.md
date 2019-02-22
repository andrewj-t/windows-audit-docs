---
title: Get IP statistics API
description: Retrieves the prevalence for the given IP.
keywords: apis, graph api, supported apis, get, ip, statistics, prevalence
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

# Get IP statistics API
**Applies to:**

- Windows Defender Advanced Threat Protection (Windows Defender ATP)

[!include[Prerelease�information](prerelease.md)]



Retrieves the prevalence for the given IP.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Windows Defender ATP APIs](apis-intro.md)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	Ip.Read.All |	'Read IP address profiles'
Delegated (work or school account) | Ip.Read.All |	'Read IP address profiles'

>[!Note]
> When obtaining a token using user credentials:
>- The user needs to have at least the following role permission: 'View Data' (See [Create and manage roles](user-roles-windows-defender-advanced-threat-protection.md) for more information)

## HTTP request
```
GET /api/ips/{ip}/stats
```

## Request headers

Name | Type | Description
:---|:---|:---
Authorization | String | Bearer {token}. **Required**.


## Request body
Empty

## Response
If successful and ip exists - 200 OK with statistical data in the body. IP do not exist - 404 Not Found.


## Example

**Request**

Here is an example of the request.

[!include[Improve request performance](improverequestperformance-new.md)]

```
GET https://api.securitycenter.windows.com/api/ips/10.209.67.177/stats
```

**Response**

Here is an example of the response.


```
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.windows.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgIPStats",
    "ipAddress": "10.209.67.177",
    "orgPrevalence": "63515",
    "orgFirstSeen": "2017-07-30T13:36:06Z",
    "orgLastSeen": "2017-08-29T13:32:59Z"
}
```
