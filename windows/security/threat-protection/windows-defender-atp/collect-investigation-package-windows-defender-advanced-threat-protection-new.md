---
title: Collect investigation package API
description: Use this API to create calls related to the collecting an investigation package from a machine.
keywords: apis, graph api, supported apis, collect investigation package
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

# Collect investigation package API

[!include[Prerelease�information](prerelease.md)]

**Applies to:**

- Windows Defender Advanced Threat Protection (Windows Defender ATP)



Collect investigation package from a machine.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Windows Defender ATP APIs](exposed-apis-intro.md)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	Machine.CollectForensics |	'Collect forensics'

## HTTP request
```
POST /api/machines/{id}/collectInvestigationPackage
```

## Request headers

Name | Type | Description
:---|:---|:---
Authorization | String | Bearer {token}. **Required**.
Content-Type | string | application/json. **Required**.

## Request body
In the request body, supply a JSON object with the following parameters:

Parameter |	Type	| Description
:---|:---|:---
Comment |	String |	Comment to associate with the action. **Required**.

## Response
If successful, this method returns 201 - Created response code and [Machine Action](machineaction-windows-defender-advanced-threat-protection-new.md) in the response body.


## Example

**Request**

Here is an example of the request.

[!include[Improve request performance](improverequestperformance-new.md)]

```
POST https://api.securitycenter.windows.com/api/machines/fb9ab6be3965095a09c057be7c90f0a2/collectInvestigationPackage
Content-type: application/json
{
  "Comment": "Collect forensics due to alert 1234"
}
```

**Response**

Here is an example of the response.

```
HTTP/1.1 201 Created
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.windows.com/api/$metadata#MachineActions/$entity",
    "id": "c9042f9b-8483-4526-87b5-35e4c2532223",
    "type": "CollectInvestigationPackage",
    "requestor": "Analyst@contoso.com",
    "requestorComment": " Collect forensics due to alert 1234",
    "status": "InProgress",
    "error": "None",
    "machineId": "f46b9bb259ed4a7fb9981b73510e3cc7aa81ec1f",
    "creationDateTimeUtc": "2017-12-04T12:09:24.1785079Z",
    "lastUpdateTimeUtc": "2017-12-04T12:09:24.1785079Z" 
}

```
