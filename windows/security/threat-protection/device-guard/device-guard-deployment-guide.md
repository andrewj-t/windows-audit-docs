---
title: Windows Defender Device Guard deployment guide (Windows 10)
description: Microsoft Windows Defender Device Guard is a feature set that consists of both hardware and software system integrity hardening features that revolutionize the Windows operating system’s security.
ms.assetid: 4BA52AA9-64D3-41F3-94B2-B87EC2717486
keywords: virtualization, security, malware
ms.prod: w10
ms.mktglfcycl: deploy
ms.localizationpriority: high
author: brianlic-msft
ms.date: 10/20/2017
---

# Windows Defender Device Guard deployment guide

**Applies to**
-   Windows 10
-   Windows Server 2016

With thousands of new malicious files created every day, using traditional methods like antivirus solutions—signature-based detection to fight against malware—provides an inadequate defense against new attacks. Windows Defender Device Guard describes a locked-down device configuration state that uses multiple enterprise-related hardware and software security features that run on Windows 10 Enterprise edition and Windows Server. When these features are configured together, Windows Defender Device Guard changes from a mode where apps are trusted unless blocked by an antivirus or other security solution, to a mode where the operating system trusts only apps authorized by your enterprise. If the app isn’t trusted, it can’t run, period. 

Windows Defender Device Guard also uses virtualization-based security to isolate the Code Integrity service and run it alongside the Windows kernel in a hypervisor-protected container. Even if an attacker manages to get control of the Windows kernel itself, the ability to run malicious executable code is much less likely. 

This guide explores the individual features in Windows Defender Device Guard as well as how to plan for, configure, and deploy them. It includes:

- [Introduction to Windows Defender Device Guard: virtualization-based security and Windows Defender Application Control](introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control.md)

- [Requirements and deployment planning guidelines for Windows Defender Device Guard](requirements-and-deployment-planning-guidelines-for-device-guard.md)

- [Planning and getting started on the Windows Defender Device Guard deployment process](planning-and-getting-started-on-the-device-guard-deployment-process.md)

- [Deploy Windows Defender Application Control](deploy-windows-defender-application-control.md)

    - [Optional: Create a code signing certificate for Windows Defender Application Control](optional-create-a-code-signing-certificate-for-windows-defender-application-control.md)

    - [Deploy Windows Defender Application Control: policy rules and file rules](deploy-windows-defender-application-control-policy-rules-and-file-rules.md)

    - [Deploy Windows Defender Application Control: steps](steps-to-deploy-windows-defender-application-control.md)

    - [Deploy catalog files to support Windows Defender Application Control](deploy-catalog-files-to-support-windows-defender-application-control.md)

- [Enable virtualization-based protection of code integrity](deploy-device-guard-enable-virtualization-based-security.md)

## Related topics

[AppLocker overview](/windows/device-security/applocker/applocker-overview)

<!-- The following topic is EIGHT YEARS OLD, but I don't really see anything better out there on Code Integrity that existed before Windows 10. -->

[Code integrity](https://technet.microsoft.com/library/dd348642.aspx)

[Protect derived domain credentials with Windows Defender Credential Guard](/windows/access-protection/credential-guard/credential-guard)

[Driver compatibility with Windows Defender Device Guard in Windows 10](https://blogs.msdn.microsoft.com/windows_hardware_certification/2015/05/22/driver-compatibility-with-device-guard-in-windows-10)

[Dropping the Hammer Down on Malware Threats with Windows 10’s Windows Defender Device Guard](https://channel9.msdn.com/Events/Ignite/2015/BRK2336)


