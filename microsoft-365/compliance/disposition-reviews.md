---
title: 处置评审概述
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 创建保留 Microsoft 365 中的内容的保留标签时，可以选择在保留期结束时触发处置评审。
ms.openlocfilehash: ee9ea34ee8527558af4d249364b539d3fa1f2fdd
ms.sourcegitcommit: 93e6bf1b541e22129f8c443051375d0ef1374150
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "42634970"
---
# <a name="overview-of-disposition-reviews"></a>处置评审概述

当内容到达其保留期结束时，您可能需要查看内容以决定是否可以安全地删除（"已释放"），这有几个原因。 例如，您可能需要执行以下操作：
  
- 在诉讼或审核的情况中，挂起相关内容的删除（"处置"）。
    
- 如果内容具有信息检索或历史值，则从处置列表中移除要存储在存档中的内容。
    
- 如果原始策略是临时或临时解决方案，则为内容分配不同的保留期。
    
- 将内容返回给客户端或将其转移到其他组织。
    
当您在 Microsoft 365 合规中心、Microsoft 365 安全中心或 Office 365 安全 & 合规性中心中创建保留标签时，您可以选择在保留期结束时触发处置评审。 在处置评审中：
  
- 您选择的人会收到一封电子邮件通知，告知他们有要审阅的内容。 请注意，每周会发送通知。
    
- 审阅者转到安全**Disposition** &amp;合规中心中的 "处置" 页面，以查看内容。 审阅者可以查看每个保留标签的项目数正在等待处置，然后选择保留标签以查看具有该标签的所有内容。
    
- 对于每个文档或电子邮件，审阅者可以执行以下操作：
    
  - 应用不同的保留标签。
    
  - 延长其保留期。
    
  - 将其永久删除。
    
- 审阅者可以查看挂起或已完成的处置，并将该列表导出为 .csv 文件。

> [!NOTE]
> 处置评审需要 Office 365 企业版 E5 订阅。
  
处置评审可以包含 Exchange 邮箱、SharePoint 网站、OneDrive 帐户和 Office 365 组中的内容。 在这些位置中等待处置评审的内容仅在审阅者选择永久删除内容后才会被删除。
  
![安全与合规中心中的处置页](../media/Retention-Dispositions-v2-page.png)


## <a name="setting-up-the-disposition-review-by-creating-a-retention-label"></a>通过创建保留标签设置处置评审

这是用于设置处置评审的基本工作流。 请注意，此流显示正在发布的保留标签，然后由用户手动应用;或者，可以将触发处置评审的保留标签自动应用于内容。
  
![显示处置的工作流的图表](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)
  
当您在 Office 365 中创建保留标签时，可以选择进行处置评审。 此选项在保留策略中不可用，但只能在配置为保留内容的保留标签中使用。
  
有关保留标签的详细信息，请参阅[保留标签概述](labels.md)。
  
![标签的保留设置](../media/a16dd202-8862-40ac-80ff-6fee974de5da.png)
 
> [!NOTE]
> 当您指定选项 "在**有准备好查看的项目时通知这些人**" 时，请指定用户。 此选项不支持 Office 365 组。

## <a name="disposing-content"></a>处置内容

当通过电子邮件通知审阅者可以查看内容时，他们可以转到安全&amp;合规性中心中的 "**处置**" 页面。 审阅者可以查看每个保留标签的项目数正在等待处置，然后选择保留标签以查看具有该标签的所有内容。

选择保留标签后，下一个页面显示该标签的所有待处理的处置。

![处置选项](../media/Retention-Disposition-options-v2.png)

然后，审阅者可以执行以下操作： 
  
- 应用不同的保留标签。
    
- 延长保留期。
    
- 永久删除项目。

请注意，审阅者可以选择多个项目并同时对其进行处置。
    
如果审阅者拥有对该位置的权限，则审阅者还可以使用该链接查看其原始位置的文档。 在处置评审过程中，内容永远不会从其原始位置移动，并且在审阅者选择执行此操作之前永远不会删除。
  
请注意，电子邮件通知将在每周的基础上自动发送给审阅者。 因此，当内容到达其保留期的末尾时，审阅者可能需要长达七天的时间才能接收到内容正在等待处置的电子邮件通知。
  
另请注意，审核所有处置操作。 为确保这一点，必须至少在第一次处置操作之前打开审核（至少一天）-有关详细信息，请参阅[在 Office 365 安全&amp;合规中心中搜索审核日志](search-the-audit-log-in-security-and-compliance.md)。 
  
## <a name="permissions-for-disposition"></a>处置权限

若要访问 "**处置**" 页面，必须为审阅者分配 "**处置管理**" 角色和 "**仅查看" 审核日志**角色。 [查看](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)有关分配角色的说明。

特定于**仅查看审核日志**角色：

- 由于用于搜索审核日志的基础 cmdlet 是 Exchange Online cmdlet，因此您必须使用 exchange [online 中的 exchange 管理中心](https://docs.microsoft.com/Exchange/exchange-admin-center)（而不是使用 Security & 合规性中心中的 "**权限**" 页）为用户分配此角色。 有关说明，请参阅[在 Exchange Online 中管理角色组](https://docs.microsoft.com/Exchange/permissions-exo/role-groups)。

- 此角色不支持 Office 365 组。 而是分配用户邮箱或邮件用户。
  
## <a name="how-long-until-disposed-content-is-permanently-deleted"></a>在永久删除已释放内容之前的时间

等待处置评审的内容仅在审阅者选择永久删除内容后才会被删除。 当审阅者选择此选项时，SharePoint 网站或 OneDrive 帐户中的内容将符合本部分中所述的标准清理过程：[保留策略如何处理就地内容](retention-policies.md#how-a-retention-policy-works-with-content-in-place)。
  
这意味着：
  
- 文档库中的内容将被移至第一阶段回收站中的**7 天内**，然后在该时间之后永久删除**93 天**。 回收站不是通过搜索编制索引，因此其内容不适用于电子数据展示保留。

- 保留保留库中的内容将在部署后的**7 天内**永久删除。

- Exchange 邮箱中的项目将在处置**前14天内**永久删除。 （请注意，14天是默认设置，但可以配置为最长30天。）
    
## <a name="view-pending-dispositions-and-disposed-items"></a>查看挂起的处置和已释放的项目

在 "**挂起的处置**" 页上，您可以查看特定保留标签的挂起和已完成的处置： 
  
- "**挂起处置**" 显示已达到其保留期并需要进行处置评审的项目。 查看每个项目后，决定是否要向其应用不同的保留标签，延长保留期，或将其永久删除。 您可以选择多个项目。
    
- "已**释放的项目**" 选项卡显示已被永久删除的项目已通过处置评审。 它们显示在这里，因为永久删除过程可能需要几天时间，如上一节中所述。 应用了不同保留标签或在审阅过程中延长保留期的项目将不会显示在此处。

![处置选项卡](../media/Retention-Disposition-tabs.png)
    
### <a name="filter-the-disposition-views"></a>筛选处置视图

您可以按保留标签或时间范围筛选这些视图。 对于挂起的处置，时间范围基于到期日期。 对于已释放的项目，时间范围基于删除日期。
  
![处置筛选器选项](../media/Retention-filter-options.png)

### <a name="export-the-disposition-items"></a>导出处置项

此外，还可以将其中一个视图中的项导出为可在 Excel 中打开的 .csv 文件。
  
![Excel 中的已导出处置数据](../media/08e3bc09-b132-47b4-a051-a590b697e725.png)
  

