---
title: Office 365 中的自动化调查和响应（空气）
keywords: 空气、autoIR、ATP、自动化、调查、响应、修正、威胁、高级、威胁、保护
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: 开始使用 Office 365 中的自动调查和响应功能高级威胁防护计划2。
ms.custom: air
ms.openlocfilehash: 45a2bc0e581916493a0170a5f86c152d02403efe
ms.sourcegitcommit: 2859c82b30ae9cbd3a3e4bcdebd65f18444f1a9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/18/2020
ms.locfileid: "42826345"
---
# <a name="automated-investigation-and-response-air-in-office-365"></a>Office 365 中的自动化调查和响应（空气）

[Office 365 高级威胁防护](office-365-atp.md)（OFFICE 365 ATP）计划2包括功能强大的自动化调查和响应（空气）功能，可节省安全运营团队的时间和精力。 随着警报的触发，安全操作团队可以对这些警报进行检查、设置优先级和响应。 跟上传入警报的数量的持续很大。 自动执行其中一些可能会有所帮助。 借助 AIR，安全操作团队可以将精力集中在优先级较高的任务上，而不会失去触发警报的可见性。

本文介绍了空气的[整体流动](#the-overall-flow-of-air)、[如何获取空中](#how-to-get-air)以及配置或使用空中功能[所需的权限](#required-permissions-to-use-air-capabilities)。 

## <a name="the-overall-flow-of-air"></a>空气的整体流动

在较高的级别，将触发警报，安全行动手册开始和自动调查，这将导致发现和建议。 下面是空中的整体流，具体步骤如下：

1. 可通过以下方式之一启动自动调查：

   - 由负责创建事件的 Office 事件触发[警报](https://docs.microsoft.com/microsoft-365/compliance/alert-policies)。 根据事件的类型，[安全行动手册](automated-investigation-response-office.md#security-playbooks)会开始进行自动调查。 

     --- 或 ---
   
   - 安全分析员在使用[威胁资源管理器](threat-explorer.md)时[开始进行自动调查](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)。

2. 在自动调查运行过程中，它将收集有关与该电子邮件相关的相关电子邮件和实体的其他数据。 此类实体可以包括文件、Url 和收件人。  调查的范围可以随着新的和相关的警报的触发而增加。

3. 在自动调查期间和之后，可以查看[详细信息和结果](air-view-investigation-results.md)。 结果包括[建议的操作](air-remediation-actions.md)，可采取这些操作来响应和修正发现的任何威胁。 此外，还可以使用[行动手册日志](air-view-investigation-results.md#playbook-log)来跟踪所有调查活动。

    如果您的组织使用的是自定义报告解决方案或第三方解决方案，则可以[使用 Office 365 管理活动 API](air-custom-reporting.md)来查看有关自动调查和威胁的信息。

4. 您的安全操作团队将检查[调查结果和建议](air-view-investigation-results.md)，并[批准或拒绝修正操作](air-review-approve-pending-completed-actions.md)。 

    在批准（或拒绝）挂起的补救措施时，自动调查完成。

> [!NOTE]
> 在 Office 365 ATP 中，不会自动执行任何修正操作。 仅在组织的安全团队进行审批时才采取更正措施。 

在自动调查过程期间和之后，安全团队可以执行以下操作：

- [查看与调查相关的警报的详细信息](air-view-investigation-results.md#view-details-about-an-alert-related-to-an-investigation)

- [查看调查的结果详细信息](air-view-investigation-results.md#view-details-of-an-investigation)

- [查看和批准作为调查结果的操作](air-review-approve-pending-completed-actions.md)

> [!TIP]
> 有关更多详细信息，请参阅[AIR 的工作原理](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office)。

## <a name="how-to-get-air"></a>如何获取空中

Office [365 高级威胁防护计划 2](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#office-365-atp-plan-1-and-plan-2)中包含 OFFICE 365 AIR 功能。 但是，[应配置 Office 365 ATP 策略](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats)，以使空气按预期方式工作。 此外，请务必查看并可能配置组织的[通知策略](https://docs.microsoft.com/microsoft-365/compliance/alert-policies)。 

Office 365 提供了许多内置的警报策略，可帮助确定 Exchange 管理员权限滥用、恶意软件活动、潜在的外部和内部威胁以及信息治理风险。 有几个[默认的警报策略](https://docs.microsoft.com/microsoft-365/compliance/alert-policies#default-alert-policies)可以触发自动调查。 其中包括以下项：

- 检测到潜在的恶意 URL 单击

- 用户将电子邮件报告为网络钓鱼

- 传递后删除包含恶意软件的电子邮件

- 传递后删除包含网络钓鱼 Url 的电子邮件

- 检测到可疑的电子邮件发送模式

- 限制用户发送电子邮件

[了解有关通知和空气的详细信息](https://docs.microsoft.com/microsoft-365/security/office-365-security/automated-investigation-response-office)。

## <a name="required-permissions-to-use-air-capabilities"></a>使用空中功能所需的权限

通过某些角色（如下表中所述的角色）授予权限： 

|任务 |需要 #a0 个角色 |
|--|--|
|设置空中功能 |以下角色之一： <br/>-全局管理员<br/>-安全管理员 <br/>可以在[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)中或在[Office 365 安全 & 合规性中心](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)中分配这些角色。 |
|批准或拒绝建议的操作|在[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)中或在[Office 365 安全 & 合规中心](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)中分配的以下角色之一：<br/>-全局管理员 <br/>-安全管理员<br/>-安全读者 <br/>--- 和 ---<br/>-搜索和清除（此角色仅在[Office 365 安全 & 合规性中心](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)中分配。 您可能需要在其中创建新的角色组，并将搜索和清除角色添加到该新角色组。

## <a name="next-steps"></a>后续步骤

- [查看自动调查的详细信息和结果](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-view-investigation-results#view-details-of-an-investigation)

- [查看和批准挂起的操作](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-remediation-actions)

## <a name="related-articles"></a>相关文章

- [Microsoft Defender 高级威胁防护中的自动化调查和修正](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [Microsoft 威胁防护中的自动调查和响应](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir)
