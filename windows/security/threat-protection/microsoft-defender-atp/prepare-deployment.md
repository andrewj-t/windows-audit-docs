---
title: Prepare Microsoft Defender ATP deployment
description: Prepare stakeholder sign-off, timelines, environment considerations, and adoption order when deploying Microsoft Defender ATP
keywords: deploy, prepare, stakeholder, timeline, environment, endpoint, server, management, adoption
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
---

# Plan Microsoft Defender ATP deployment

**Applies to:**
- [Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP)](https://go.microsoft.com/fwlink/p/?linkid=2069559)




Deploying Microsoft Defender ATP is a three-phase process:

<br>
<table border="0" width="100%" align="center">
  <tr style="text-align:center;">
    <td align="center" style="width:25%; border:0;" bgcolor="#d5f5e3">
      <a href= "prepare-deployment"> 
        <img src="images/plan.png" alt="Plan to deploy Microsoft Defender ATP" title="Plan" />
      <br/>Plan </a><br>
    </td>
     <td align="center"  >
      <a href="production-deployment">
        <img src="images/oboard.png" alt="Onboard to the Microsoft Defender ATP service" title="Onboard to Microsoft Defender ATP" />
      <br/> Onboard </a><br>
        </td>
    <td align="center">
      <a href="configure">
        <img src="images/configure.png" alt="Configure capabilities" title="Configure capabilities" />
      <br/>Configure </a><br>
</td>
  </tr>
  <tr>
    <td style="width:25%; border:0;">
   
    </td>
    <td valign="top" style="width:25%; border:0;">
    
</td>
    <td valign="top" style="width:25%; border:0;">

</td>    
  </tr>
</table>

You are currently in the planning phase.

![Icons](images/plan-page.png)







## Stakeholders and Sign-off
The following section serves to identify all the stakeholders that are involved
in this project and need to sign-off, review, or stay informed. Add stakeholders
to the table below as appropriate for your organization.

-   SO = Sign-off on this project

-   R = Review this project and provide input

-   I = Informed of this project

| Name                 | Role                                                                                                                                                                                                          | Action |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|
| Enter name and email | **Chief Information Security Officer (CISO)** *An executive representative who serves as sponsor inside the organization for the new technology deployment.*                                                  | SO     |
| Enter name and email | **Head of Cyber Defense Operations Center (CDOC)** *A representative from the CDOC team in charge of defining how this change is aligned with the processes in the customers security operations team.*       | SO     |
| Enter name and email | **Security Architect** *A representative from the Security team in charge of defining how this change is aligned with the core Security architecture in the organization.*                         | R      |
| Enter name and email | **Workplace Architect** *A representative from the IT team in charge of defining how this change is aligned with the core workplace architecture in the organization.*                             | R      |
| Enter name and email | **Security Analyst** *A representative from the CDOC team who can provide input on the detection capabilities, user experience and overall usefulness of this change from a security operations perspective.* | I      |

## Project Management

### In Scope

The following is in scope for this project:

-   Enabling Microsoft Defender ATP endpoint protection platform (EPP)
    capabilities

    -   Next Generation Protection

    -   Attack Surface Reduction

-   Enabling Microsoft Defender ATP endpoint detection and response (EDR)
    capabilities including automatic investigation and remediation

-   Enabling Microsoft Defender ATP threat and vulnerability management (TVM)
-   Use of System Center Configuration Manager to onboard endpoints into the service.

### Out of scope

The following are out of scope of this project:

-   Configuration of third-party solutions that might integrate with Microsoft
    Defender ATP.

-   Penetration testing in production environment.

## Environment 


This section is used to ensure your environment is deeply understood by the
stakeholders which will help identify potential dependencies and/or changes
required in technologies or processes.

| What                                  | Description |
|---------------------------------------|-------------|
| Endpoint count                        |             |
| Server count                          |             |
| Management engine                     |             |
| CDOC distribution                     |             |
| Security information and event (SIEM) |             |


## Role-based access control

Microsoft recommends using the concept of least privileges. Microsoft Defender
ATP leverages built-in roles within Azure Active Directory. Microsoft recommend
[review the different roles that are
available](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal)
and choose the right one to solve your needs for each persona for this
application. Some roles may need to be applied temporarily and removed after the
deployment has been completed.

| Personas                     | Roles | Azure AD Role (if required) | Assign to |
|------------------------------|-------|-----------------------------|-----------|
| Security Administrator       |       |                             |           |
| Security Analyst             |       |                             |           |
| Endpoint Administrator       |       |                             |           |
| Infrastructure Administrator |       |                             |           |
| Business Owner/Stakeholder   |       |                             |           |

Microsoft recommends using [Privileged Identity
Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure)
to manage your roles to provide additional auditing, control, and access review
for users with directory permissions.

Microsoft Defender ATP supports two ways to manage permissions:

-   **Basic permissions management**: Set permissions to either full access or
    read-only. In the case of basic permissions management users with Global
    Administrator or Security Administrator role in Azure Active Directory have
    full access while the Security reader role has read-only access.

-   **Role-based access control (RBAC)**: Set granular permissions by defining
    roles, assigning Azure AD user groups to the roles, and granting the user
    groups access to machine groups. For more information. see [Manage portal access using role-based access control](rbac.md).

Microsoft recommends leveraging RBAC to ensure that only users that have a
business justification can access Microsoft Defender ATP.

You can find details on permission guidelines
[here](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/user-roles#create-roles-and-assign-the-role-to-an-azure-active-directory-group).

The following example table serves to identify the Cyber Defense Operations
Center structure in your environment that will help you determine the RBAC
structure required for your environment.

| Tier   | Description                                                                                                                                                                                                 | Permission Required |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| Tier 1 | **Local security operations team / IT team**<br>This team usually triages and investigates alerts contained within their geolocation and escalates to Tier 2 in cases where an active remediation is required.                                              |                     |
| Tier 2 | **Regional security operations team**<br>This team can see all the machines for their region and perform remediation actions.                                                                                                                        |        View data               |
| Tier 3 | **Global security operations team**<br>This team consists of security experts and are authorized to see and perform all actions from the portal. | View data <br>  Alerts investigation Active remediation actions <br> Alerts investigation Active remediation actions <br> Manage portal system settings <br> Manage security settings |



## Adoption Order
In many cases organizations will have existing endpoint security products in
place. The bare minimum every organization should have is an antivirus solution. But in some cases an organization might also already implanted an EDR solution.
Historically, replacing any security solution was time intensive and difficult
to achieve due to the tight hooks into the application layer and infrastructure
dependencies. However, because Microsoft Defender ATP is built into the
operating system, replacing third-party solutions is easy to achieve.

Choose which component of Microsoft Defender ATP to be used and remove the ones
that do not apply. The table below indicates the Microsoft recommendation on the
order on how the endpoint security suite should be enabled.

| Component                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Adoption Order Rank |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| Endpoint Detection & Response (EDR)     | Microsoft Defender ATP endpoint detection and response capabilities provide advanced attack detections that are near real-time and actionable. Security analysts can prioritize alerts effectively, gain visibility into the full scope of a breach, and take response actions to remediate threats. [Learn more.](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/overview-endpoint-detection-response)                                                                                                                                                                                                                                             | 1                   |
| Next Generation Protection (NGP)        | Microsoft Defender Antivirus is a built-in antimalware solution that provides next generation protection for desktops, portable computers, and servers. Windows Defender Antivirus includes:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | 2                   |
| Attack Surface Reduction (ASR)          | Attack surface reduction capabilities in Microsoft Defender ATP helps protect the devices and applications in the organization from new and emerging threats. [Learn more.](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/overview-attack-surface-reduction)                                                                                                                                                                                                                                                                                                                                                                                       | 3                   |
| Threat & Vulnerability Management (TVM) | Threat & Vulnerability Management is a component of Microsoft Defender ATP, and provides both security administrators and security operations teams with unique value, including:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 4                   |
| Auto Investigation & Remediation (AIR)  | Microsoft Defender ATP uses Automated investigations to significantly reduce the volume of alerts that need to be investigated individually. The Automated investigation feature leverages various inspection algorithms, and processes used by analysts (such as playbooks) to examine alerts and take immediate remediation action to resolve breaches. This significantly reduces alert volume, allowing security operations experts to focus on more sophisticated threats and other high value initiatives. [Learn more.](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/automated-investigations-windows-defender-advanced-threat-protection) | Not applicable      |
| Microsoft Threat Experts (MTE)          | Microsoft Threat Experts is a managed hunting service that provides Security Operation Centers (SOCs) with expert level monitoring and analysis to help them ensure that critical threats in their unique environments don't get missed. [Learn more.](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/microsoft-threat-experts)                                                                                                                                                                                                                                                                                                                     | Not applicable      |

## Related topic
- [Production deployment](production-deployment.md)