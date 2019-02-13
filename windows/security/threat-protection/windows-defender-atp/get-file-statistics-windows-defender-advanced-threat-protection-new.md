---
title: Get file statistics API
description: Retrieves the prevalence for the given file.
keywords: apis, graph api, supported apis, get, file, statistics
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

# Get file statistics API
**Applies to:**

- Windows Defender Advanced Threat Protection (Windows Defender ATP)

[!include[Prerelease�information](prerelease.md)]





Retrieves the prevalence for the given file.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Windows Defender ATP APIs](apis-intro.md)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	File.Read.All |	'Read file profiles'
Delegated (work or school account) | File.Read.All | 'Read file profiles'

>[!Note]
> When obtaining a token using user credentials:
>- The user needs to have at least the following role permission: 'View Data' (See [Create and manage roles](user-roles-windows-defender-advanced-threat-protection.md) for more information)

## HTTP request
```
GET /api/files/{id}/stats
```

## Request headers

Name | Type | Description
:---|:---|:---
Authorization | String | Bearer {token}. **Required**.


## Request body
Empty

## Response
If successful and file exists - 200 OK with statistical data in the body. If file do not exist - 404 Not Found.


## Example

**Request**

Here is an example of the request.

[!include[Improve request performance](improverequestperformance-new.md)]

```
GET https://api.securitycenter.windows.com/api/files/6532ec91d513acc05f43ee0aa3002599729fd3e1/stats
```

**Response**

Here is an example of the response.


```
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.windows.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgFileStats",
    "sha1": "6532ec91d513acc05f43ee0aa3002599729fd3e1",
    "orgPrevalence": "3",
    "orgFirstSeen": "2018-07-15T06:13:59Z",
    "orgLastSeen": "2018-08-03T16:45:21Z",
    "topFileNames": [
        "chrome_1.exe",
		"chrome_2.exe"
    ]
}

```
