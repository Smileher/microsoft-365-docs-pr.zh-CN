---
title: 还原已删除的 Office 365 组
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: 了解如何还原已删除的 Office 365 组。
ms.openlocfilehash: 31d6481f87d7da219e042eefa8f004425caee133
ms.sourcegitcommit: 1883a103449d7b03d482228bd9ef39a7caf306cf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "42583159"
---
# <a name="restore-a-deleted-office-365-group"></a>还原已删除的 Office 365 组

如果已删除某个组，默认情况下它将保留30天。 这30天的期限被视为 "软删除"，因为您仍可以还原组。 30天后，该组及其关联的内容将被永久删除且无法还原。

还原组时，还可还原以下内容：
  
- Azure Active Directory （AD） Office 365 组对象、属性和成员。
    
- 组的电子邮件地址。
    
- Exchange Online 共享的收件箱和日历。
    
- SharePoint Online 团队网站和文件。
    
- OneNote 笔记本
    
- Planner
    
- Teams

- Yammer 组和组内容（如果已从 Yammer 创建了 Office 365 组）

## <a name="restore-a-group-that-you-own-by-using-outlook"></a>使用 Outlook 还原您拥有的组

如果您是 Office 365 组的所有者，则可以通过执行以下步骤在 Outlook 中自行还原组：

1. 在 "[已删除的组" 页](https://outlook.office.com/people/group/deleted)上，选择 "**组**" 节点下的 "**管理组**" 选项，然后选择 "**已删除**"。
2. 单击要还原的组旁边的 "**还原**" 选项卡。

如果此处未显示已删除的组，请与管理员联系。

## <a name="restore-a-group-in-the-microsoft-365-admin-center"></a>在 Microsoft 365 管理中心中还原组

如果您是全局管理员或组管理员，则可以在 Microsoft 365 管理中心中还原已删除的组：

1. 转到位于 [https://admin.microsoft.com](Go to the admin center at https://admin.microsoft.com) 的管理中心。
2. 展开 "**组**"，然后单击 "**已删除组**"。
3. 选择要还原的组，然后单击 "**还原组**"。
  
## <a name="permanently-delete-an-office-365-group"></a>永久删除 Office 365 组

有时，您可能希望永久清除组，而无需等待30天软删除期过期。 若要执行此操作，启动 PowerShell 并运行此命令，获取组的对象 ID：
  
```
Get-AzureADMSDeletedGroup
```

记下要永久删除的一个或几个组的对象 ID。
  
> [!CAUTION]
> 清除组后可永久删除该组及其数据。 
  
若要清除组，请在 PowerShell 中运行此命令：
  
```
Remove-AzureADMSDeletedDirectoryObject -Id <objectId>
```

若要确认是否成功清除该组，请再次运行  *Get-AzureADMSDeletedGroup*  cmdlet 以确认该组不再出现在软删除的组列表中。某些情况下，要永久删除该组及其所有数据可能需要长达 24 小时。 
  
## <a name="got-questions-about-office-365-groups"></a>对 Office 365 组有疑问？

访问[Microsoft 技术社区](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups)以发布问题并参与有关 Office 365 组的对话。 
  
## <a name="related-articles"></a>相关文章

[使用 PowerShell 管理 Office 365 组](https://support.office.com/article/aeb669aa-1770-4537-9de2-a82ac11b0540)
  
[使用 Remove-UnifiedGroup cmdlet 删除组](https://technet.microsoft.com/library/mt238270%28v=exchg.160%29.aspx)
  
[管理连接了组的团队网站设置](https://support.office.com/article/8376034d-d0c7-446e-9178-6ab51c58df42.aspx)
  
[在 Outlook 中删除组](https://support.office.com/article/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f.aspx)
