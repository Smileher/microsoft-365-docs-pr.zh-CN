---
title: 启用或禁用 Office 365 审核日志搜索
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: e893b19a-660c-41f2-9074-d3631c95a014
description: 您可以在安全 & 合规性中心启用审核日志搜索功能。 如果你更改了想法，你可以随时关闭。 当 "审核日志搜索" 关闭时，管理员无法在组织中搜索用户和管理员活动的 Office 365 审核日志。
ms.openlocfilehash: 4e5a8c3236da9d2cf6e9392b8a9a29d064b0ce0d
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2020
ms.locfileid: "42069415"
---
# <a name="turn-office-365-audit-log-search-on-or-off"></a>启用或禁用 Office 365 审核日志搜索

您（或另一个管理员）必须先启用审核日志记录，然后才能开始搜索 Office 365 审核日志。 如果启用了安全 & 合规中心中的审核日志搜索，则组织中的用户和管理员活动将记录在审核日志中，并在90天内保留。 但是，您的组织可能不想记录和保留审核日志数据。 或者，您可能使用第三方安全信息和事件管理（SIEM）应用程序访问您的审核数据。 在这些情况下，全局管理员可以在 Office 365 中关闭审核日志搜索。
  
## <a name="before-you-begin"></a>开始之前

- 您必须在 Exchange Online 中向您分配 "审核日志" 角色，才能在 Office 365 组织中打开或关闭审核日志搜索。 默认情况下，此角色在 Exchange 管理中心中的 "**权限**" 页上分配给合规性管理和组织管理角色组。 Office 365 中的全局管理员是 Exchange Online 中的 "组织管理" 角色组的成员。 
    
    > [!IMPORTANT]
    > 必须在 Exchange Online 中向用户分配权限，才能打开或关闭审核日志搜索。 如果您在安全 & 合规中心中向用户分配 "**权限**" 页上的 "审核日志" 角色，则他们将无法打开或关闭审核日志搜索。 这是因为基础 cmdlet 是 Exchange Online cmdlet。 
  
- 如果关闭了 Office 365 中的审核日志搜索，则不能使用 Office 365 管理活动 API 访问组织的审核数据。 按照本文中的步骤关闭审核日志搜索意味着，在使用 Security & 合规中心或在 Exchange Online PowerShell 中运行**UnifiedAuditLog** cmdlet 时，搜索审核日志时不会返回任何结果。 这也意味着你的审核日志将无法通过 Office 365 管理活动 API 提供。  
    
- 有关搜索 Office 365 审核日志的分步说明，请参阅[在安全 & 合规性中心中搜索审核日志](search-the-audit-log-in-security-and-compliance.md)。
    
## <a name="turn-on-audit-log-search"></a>启用审核日志搜索

您可以使用安全 & 合规性中心或 PowerShell 在 Office 365 中启用审核日志搜索。 在您打开审核日志搜索后，可能需要几个小时才能在搜索审核日志时返回结果。 您必须在 Exchange Online 中向您分配 "审核日志" 角色，才能启用审核日志搜索。
  
### <a name="use-the-security--compliance-center-to-turn-on-audit-log-search"></a>使用安全 & 合规性中心启用审核日志搜索

1. 在 "安全性 & 合规性中心中，转到"**搜索** \> **审核日志搜索**"。
    
   将显示一个横幅，指出审核必须打开以记录用户和管理员活动。

2. 单击 "**启用审核"**。
    
    ![单击 "启用审核"](../media/39a9d35f-88d0-4bbe-a962-0be2f838e2bf.png)
  
    标题已更新，指示审核日志正在准备，并且您可以在几个小时内搜索用户和管理活动。
    
### <a name="use-powershell-to-turn-on-audit-log-search"></a>使用 PowerShell 打开审核日志搜索

1. [连接到 Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=396554)
    
2. 运行以下 PowerShell 命令以在 Office 365 中启用审核日志搜索。
    
    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    将显示一条消息，指出可能需要长达60分钟的时间才能使更改生效。
  
## <a name="turn-off-audit-log-search"></a>关闭审核日志搜索

您必须使用连接到 Exchange Online 组织的远程 PowerShell，才能关闭审核日志搜索。 与启用审核日志搜索类似，您必须在 Exchange Online 中将 "审核日志" 角色分配给 "关闭审核日志搜索"。
  
1. [连接到 Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=396554)
    
2. 运行以下 PowerShell 命令以关闭 Office 365 中的审核日志搜索。
    
    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. 一段时间后，验证审核日志搜索是否已关闭（已禁用）。 可通过 2 种方法执行此操作：
    
    - 在 PowerShell 中，运行以下命令：

    ```powershell
    Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
    ```

      UnifiedAuditLogIngestionEnabled 属性的`False`值指示__ 已关闭审核日志搜索。 
    
    - 在 "安全性 & 合规性中心中，转到"**搜索** \> **审核日志搜索**"。
    
      将显示一条横幅，指出必须打开审核才能记录用户和管理员活动。
