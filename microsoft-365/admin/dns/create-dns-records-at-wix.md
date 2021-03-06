---
title: 在 Wix 上为 Office 365 创建 DNS 记录
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: 了解如何在 Wix for Office 365 中验证您的域并为电子邮件、Skype for Business Online 和其他服务设置 DNS 记录。
ms.openlocfilehash: 43d2f2417153dd0c848c33736733237b1681c02c
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/24/2020
ms.locfileid: "42238551"
---
# <a name="create-dns-records-at-wix-for-office-365"></a>在 Wix 上为 Office 365 创建 DNS 记录

 如果找不到要查找的内容，请**[查看域常见问题解答](../setup/domains-faq.md)**。 
  
如果 Wix 是您的 DNS 托管提供商，请按照本文中的步骤验证您的域并为电子邮件、Skype for Business Online 等设置 DNS 记录。
  
下面是要添加的主要记录。 
  
- [添加 TXT 记录进行验证](#add-a-txt-record-for-verification)。
    
- [添加 MX 记录，以便您的域的电子邮件将进入 Office 365](#add-an-mx-record-so-email-for-your-domain-will-come-to-office-365)。
    
- [添加 Office 365 所需的五个 CNAME 记录](#add-the-five-cname-records-that-are-required-for-office-365)。
    
- [为 SPF 添加 TXT 记录以帮助防止垃圾邮件](#add-a-txt-record-for-spf-to-help-prevent-email-spam)。
    
- [添加 Office 365 所需的两条 SRV 记录](#add-the-two-srv-records-that-are-required-for-office-365)。
    
在 Wix 中添加这些记录后，您的域将设置为与 Office 365 服务配合使用。
  
> [!NOTE]
>  DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。 
  
## <a name="add-a-txt-record-for-verification"></a>添加 TXT 记录进行验证
<a name="BKMK_txt"> </a>

在将域用于 Office 365 之前，必须确保你拥有该域。如果你能够在域注册机构处登录到你的帐户并创建 DNS 记录，便可向 Office 365 证明你是所有者。
  
> [!NOTE]
> 此记录仅用于验证您是否拥有自己的域；它不会影响其他任何内容。 如果需要，您可以以后将其删除。 
  
1. 若要开始，请使用[此链接](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account)转到 Wix 上的 "域" 页面。 You'll be prompted to log in first.
    
2. 在 "**我的域**" 页面上的 "**高级**" 区域中，选择 "**编辑 DNS** " 按钮。 
    
3. 在 DNS 编辑器的**TXT （文本）** 行中选择 " **+ 添加另一个**"。 
    
4. In the boxes for the new record, type or copy and paste the values from the following table. 
    
||||
|:-----|:-----|:-----|
|**Host Name** <br/> |**TXT Value** <br/> |**TTL** <br/> |
|自动填充  <br/> |MS=ms *XXXXXXXX*  <br/> **注意：** 这是一个示例。 在这里使用来自 Office 365 中的表的特定" **目标或指向的地址**"值。  [如何查找此内容？](../get-help-with-domains/information-for-dns-records.md)|1 小时 <br/> |          |
   
5. 选择 DNS 编辑器顶部的 "**保存 DNS** " 按钮。 
    
6. 请在继续之前等待数分钟，以便您刚刚创建的记录可以通过 Internet 完成更新。
    
Now that you've added the record at your domain registrar's site, you'll go back to Office 365 and request Office 365 to look for the record.
  
When Office 365 finds the correct TXT record, your domain is verified.
  
1. 在管理中心中，转到 "**设置** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">域</a>" 页。
    
2. 在 "**域**" 页上，选择要验证的域。 
  
  
3. 在 "**设置**" 页上，选择 "**启动安装程序**"。
   
  
4. 在 "**验证域**" 页上，选择 "**验证**"。
    
    
  
> [!NOTE]
>  DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>添加一条 MX 记录，确保发往您的域的电子邮件发送到 Office 365
<a name="BKMK_mx"> </a>

1. 若要开始，请使用[此链接](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account)转到 Wix 上的 "域" 页面。 You'll be prompted to log in first.
    
2. 在 "**我的域**" 页面上的 "**邮箱**" 区域中，选择 "**配置您的 MX 记录**" 链接。 
    
3. 从 "**电子邮件提供商**" 下拉列表中选择 "**其他**"。 
    
4. 选择 " **+ 添加另一个**"。
    
5. 在新记录的框中，键入或复制并粘贴下表中的值：
    
|**Host Name**|**Points to **|**优先级**|**TTL**|
|:-----|:-----|:-----|:-----|
|自动填充 <br/> | *\<域密钥\>*  .mail.protection.outlook.com  <br/> **注意：** 从 Office 365 帐户中获取你* \<的域密钥\> * 。   如何查找此内容？[](../get-help-with-domains/information-for-dns-records.md) |0  <br/> 有关优先级的详细信息，请参阅[什么是 MX 优先级？](https://support.office.com/article/What-is-MX-priority-2784cc4d-95be-443d-b5f7-bb5dd867ba83) | 1 Hour|
   
6. 如果列出了任何其他 MX 记录，请将其删除。 
    
7. 选择“**确定**”。
    
8. 在确认对话框中，选择 **"确定"**。
    
## <a name="add-the-five-cname-records-that-are-required-for-office-365"></a>添加 Office 365 所需的五个 CNAME 记录
<a name="BKMK_cname"> </a>

1. 若要开始，请使用[此链接](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account)转到 Wix 上的 "域" 页面。 You'll be prompted to login first.
    
2. 在 "**我的域**" 页面上的 "**高级**" 区域中，选择 "**编辑 DNS** " 按钮。 
    
3. 在 DNS 编辑器的 " **cname （别名）** " 行中选择 "+ 向每个 Cname 记录**添加另一个**"。 
    
4. 在新记录的框中，键入或复制并粘贴下表中的值：
    
|**Host Name**|**Points to **|**TTL**|
|:-----|:-----|:-----|
|autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 Hour  <br/> |
|sip  <br/> |sipdir.online.lync.com  <br/> |1 Hour <br/> |
|lyncdiscover  <br/> |webdir.online.lync.com   <br/> |1 Hour  <br/> |
|enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |1 Hour <br/> |
|enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |1 Hour  <br/> |
   
5. 选择 DNS 编辑器顶部的 "**保存 DNS** " 按钮。 
    
6. Wait a few minutes before you continue, so that the record you just created can update across the Internet.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>为 SPF 添加 TXT 记录以帮助防止垃圾邮件
<a name="BKMK_spf"> </a>

> [!IMPORTANT]
> You cannot have more than one TXT record for SPF for a domain. If your domain has more than one SPF record, you'll get email errors, as well as delivery and spam classification issues. If you already have an SPF record for your domain, don't create a new one for Office 365. 改为将所需的 Office 365 值添加到当前记录，以便您具有包含两组值的*单个*SPF 记录。  
  
1. 若要开始，请使用[此链接](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account)转到 Wix 上的 "域" 页面。 You'll be prompted to log in first.
    
2. 在 "**我的域**" 页面上的 "**高级**" 区域中，选择 "**编辑 DNS** " 按钮。 
    
3. 在 DNS 编辑器的**TXT （文本）** 行中选择 " **+ 添加另一个**"。 
    
4. 在新记录的框中，键入或复制并粘贴下表中的值：
    
|**Host Name**|**TXT Value**|**TTL**|
|:-----|:-----|:-----|
|[保留此空白]  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **注意：** 我们建议您复制并粘贴此条目，以确保所有的间距保持正确。<br/> |TXT  <br/> | 1 Hour |
   
5. 选择 DNS 编辑器顶部的 "**保存 DNS** " 按钮。 
    
6. Wait a few minutes before you continue, so that the record you just created can update across the Internet.
    
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>添加 Office 365 所需的两条 SRV 记录
<a name="BKMK_srv"> </a>

1. 若要开始，请使用[此链接](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account)转到 Wix 上的 "域" 页面。 You'll be prompted to log in first.
    
2. 在 "**我的域**" 页面上的 "**高级**" 区域中，选择 "**编辑 DNS** " 按钮。 
    
3. 在 DNS 编辑器的**SRV**行中选择 " **+ 添加另一个**"。 
    
4. 在新记录的框中，键入或复制并粘贴下表中的值：
    
|**服务**|**协议**|**名称**|**权重**|**端口**|**目标**|**优先级**|**TTL**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|sip  |tls  |自动填充 |1  |443   |sipdir.online.lync.com |100 |1 Hour |
|sipfed.online.lync.com>|tcp |自动填充|1 |5061 |sipfed.online.lync.com|100 | 1 Hour |
   
5. 选择 DNS 编辑器顶部的 "**保存 DNS** " 按钮。 
    
6. Wait a few minutes before you continue, so that the record you just created can update across the Internet.
    
> [!NOTE]
>  DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。 
  

