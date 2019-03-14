---
title: List Indicators API
description: Use this API to create calls related to get Indicators collection
keywords: apis, public api, supported apis, Indicators collection
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

# List Indicators API

**Applies to:** - Windows Defender Advanced Threat Protection (Windows Defender ATP)

[!include[Prerelease�information](prerelease.md)]

>[!Note]
> Currently this API is supported only for AppOnly context requests. (See [Get access with application context](exposed-apis-create-app-webapp.md) for more information)


- Gets collection of TI Indicators.
- Get TI Indicators collection API supports [OData V4 queries](https://www.odata.org/documentation/).

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Get started](apis-intro.md)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	Ti.ReadWrite |	'Read and write Indicators'
Application |	Ti.ReadWrite.All |	'Read and write All Indicators'


## HTTP request
```
GET https://api.securitycenter.windows.com/api/indicators
```

[!include[Improve request performance](improverequestperformance-new.md)]

## Request headers

Name | Type | Description
:---|:---|:---
Authorization | String | Bearer {token}. **Required**.


## Request body
Empty

## Response
If successful, this method returns 200, Ok response code with a collection of [Indicator](ti-indicator-windows-defender-advanced-threat-protection-new.md) entities.

>[!Note]
> If the Application has 'Ti.ReadWrite.All' permission, it will be exposed to all Indicators. otherwise, it will be exposed only to the Indicators it created.

## Example

**Request**

Here is an example of a request that gets all TI Indicators

```
GET https://api.securitycenter.windows.com/api/indicators
```

**Response**

Here is an example of the response.

```
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.windows.com/api/$metadata#Indicators",
    "value": [
        {
            "indicatorValue": "12.13.14.15",
            "indicatorType": "IpAddress",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T11:15:35.3688259Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "action": "AlertAndBlock",
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "test",
			"rbacGroupNames": []
        },
        {
            "indicatorValue": "220e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "action": "AlertAndBlock",
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
			"rbacGroupNames": [ "Group1", "Group2" ]
        }
    ]
}
```
