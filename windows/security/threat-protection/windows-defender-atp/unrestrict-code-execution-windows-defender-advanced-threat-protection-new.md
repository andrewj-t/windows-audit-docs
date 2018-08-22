---
title: Remove app restriction API
description: Use this API to create calls related to removing a restriction from applications from executing.
keywords: apis, graph api, supported apis, remove machine from isolation
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

# Remove app restriction API

**Applies to:**

- Windows Defender Advanced Threat Protection (Windows Defender ATP)



Enable execution of any application on the machine.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Windows Defender ATP APIs](exposed-apis-intro.md)

Permission type |	Permission	|	Permission display name
:---|:---|:---
Application |	Machine.RestrictExecution |	'Restrict code execution'
Delegated (work or school account) | Machine.RestrictExecution | 'Restrict code execution'

## HTTP request
```
POST /api/machines/{id}/unrestrictCodeExecution
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
Comment |	String | Comment to associate with the action. **Required**.

## Response
If successful, this method returns 201 - Created response code and [Machine Action](machineaction-windows-defender-advanced-threat-protection-new.md) in the response body.


## Example

**Request**

Here is an example of the request.

[!include[Improve request performance](improverequestperformance-new.md)]

```
POST https://api.securitycenter.windows.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/unrestrictCodeExecution 
Content-type: application/json
{
  "Comment": "Unrestrict code execution since machine was cleaned and validated"
}

```

**Response**

Here is an example of the response.

```
HTTP/1.1 201 Created
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.windows.com/api/$metadata#MachineActions/$entity",
    "id": "44cffc15-0e3d-4cbf-96aa-bf76f9b27f5e",
    "type": "UnrestrictCodeExecution",
    "requestor": "Analyst@contoso.com",
    "requestorComment": "Unrestrict code execution since machine was cleaned and validated ",
    "status": "InProgress",
    "error": "None",
    "machineId": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
    "creationDateTimeUtc": "2017-12-04T12:15:40.6052029Z",
    "lastUpdateTimeUtc": "2017-12-04T12:15:40.6052029Z"
}

```

To restrict code execution on a machine, see [Restrict app execution](restrict-code-execution-windows-defender-advanced-threat-protection-new.md).