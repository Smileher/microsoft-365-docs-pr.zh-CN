---
title: 在 name.com 处为 Office 365 创建 DNS 记录
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
ms.assetid: 9ddcc2fc-9433-4335-8192-6ffb1f541087
description: 了解如何在 name.com for Office 365 中验证您的域并为电子邮件、Skype for Business Online 和其他服务设置 DNS 记录。
ms.openlocfilehash: f21a40f543ff3a9faffe6ffba98f4d541b2a7a7b
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2020
ms.locfileid: "42349970"
---
# <a name="create-dns-records-at-namecom-for-office-365"></a>在 name.com 处为 Office 365 创建 DNS 记录

 **如果找不到要查找的内容，请[查看域常见问题解答](../setup/domains-faq.md)** 。 
  
如果 DNS 托管提供者是 name.com，请按本文中的步骤验证域并为电子邮件、Skype for Business Online 等设置 DNS 记录。
  
在 name.com 添加这些记录后，域将设置为使用 Office 365 服务。
  
若要了解如何与 Office 365 结合使用网站的 Web 宿主和 DNS，请参阅[配合使用公共网站与 Office 365](https://support.office.com/article/choose-a-public-website-3325d50e-d131-403c-a278-7f3296fe33a9)。
  
> [!NOTE]
> DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。 
  
## <a name="add-a-txt-record-for-verification"></a>添加 TXT 记录进行验证
<a name="BKMK_verify"> </a>

在将域用于 Office 365 之前，必须确保你拥有该域。如果你能够在域注册机构处登录到你的帐户并创建 DNS 记录，便可向 Office 365 证明你是所有者。
  
> [!NOTE]
> 此记录仅用于验证您是否拥有自己的域；它不会影响其他任何内容。 如果需要，您可以以后将其删除。 
  
1. 若要开始，请使用[此链接](https://www.name.com/account/domain)转到 name.com 上你的域页面。系统将会提示你首先登录。
    
    ![Name-BP-Configure-1-1](../../media/1869b416-1d3f-4fb1-99c6-62b74ca7a4c7.png)
  
2. 在 **"我的域**" 下，选择要修改的域的名称。
    
    ![Name-BP-Configure-1-2](../../media/c8b96e1e-aa35-4fb1-8209-450f587fec4d.png)
  
3. 在 "**详细信息**" 列中，选择 "* * DNS 记录 * *"。 
    
    ![Name-BP-Configure-1-3](../../media/c5da31e2-2f77-4d0c-b31d-189e6fb7b205.png)
  
4. 在新记录的框中，键入或复制并粘贴下表中的值。
    
    (Choose the **Type** value from the drop-down list.) 
    
    |||||
    |:-----|:-----|:-----|:-----|
    |**类型** <br/> |**主机** <br/> |**应答** <br/> |**TTL** <br/> |
    |TXT  <br/> |(Leave this field empty.)  <br/> |MS=ms *XXXXXXXX*  <br/> **注意：** 此为示例。 在这里使用来自 Office 365 中的表的具体**目标地址或指向的地址**值。           [如何查找此项？](../get-help-with-domains/information-for-dns-records.md)          |Use the default value (300).  <br/> |
   
    ![Name-BP-Verify-1-1](../../media/0c352fd3-cf84-439f-a481-0705e225cc54.png)
  
5. 选择 "**添加记录**"。
    
    ![Name-BP-Verify-1-2](../../media/816fc60b-17ab-4982-8849-6c3fcf3ca3d6.png)
  
6. 请在继续之前等待数分钟，以便您刚刚创建的记录可以通过 Internet 完成更新。
    
现在你已在域注册机构网站添加了记录，然后将返回到 Office 365 并请求 Office 365 查找记录。
  
Office 365 找到正确的 TXT 记录时，表明你的域已通过验证。
  
1. 在管理中心，转到“**设置**”\> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">域</a>页面。
    
2. 在“**域**”页面上，选择要验证的域。 
    
    
  
3. 在“**设置**”页面上，选择“**开始设置**”。
    
    
  
4. 在“**验证域**”页面上，选择“**验证**”。
    
    
  
> [!NOTE]
> DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-office-365"></a>添加一条 MX 记录，确保发往你的域的电子邮件发送到 Office 365
<a name="BKMK_add_MX"> </a>

1. 若要开始，请使用[此链接](https://www.name.com/account/domain)转到 name.com 上你的域页面。系统将会提示你首先登录。
    
    ![Name-BP-Configure-1-1](../../media/1869b416-1d3f-4fb1-99c6-62b74ca7a4c7.png)
  
2. 在 **"我的域**" 下，选择要修改的域的名称。
    
    ![Name-BP-Configure-1-2](../../media/c8b96e1e-aa35-4fb1-8209-450f587fec4d.png)
  
3. 在 "**详细信息**" 列中，选择 " **DNS 记录**"。 
    
    ![Name-BP-Configure-1-3](../../media/c5da31e2-2f77-4d0c-b31d-189e6fb7b205.png)
  
4. 在新记录的框中，键入或复制并粘贴下表中的值。
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**类型**|**主机**|**应答**|**TTL**|**优先级**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX  <br/> |（将此字段留空。）  <br/> | *\<域密钥\>*  .mail.protection.outlook.com  <br/> **注意：** 从 Office 365 帐户中获取你* \<的域密钥\> * 。           [如何查找此内容？](../get-help-with-domains/information-for-dns-records.md)          |Use the default value (300).  <br/> |0  <br/> 有关优先级的详细信息，请参阅[什么是 MX 优先级？](https://support.office.com/article/2784cc4d-95be-443d-b5f7-bb5dd867ba83.aspx) <br/> |
   
   ![Name-BP-Configure-2-1](../../media/11ba2160-fc8e-4196-bb15-2b7c6d49c8fc.png)
  
5. 选择 "**添加记录**"。
    
    ![Name-BP-Configure-2-2](../../media/fd09f161-7cc4-4723-aec2-5fa801bd19e9.png)
  
6. 如果存在任何其他 MX 记录，请使用以下两步操作删除这些记录：
    
    对于每个其他 MX 记录，请在 "**操作**" 列中选择 "**删除**"。 
    
    ![Name-BP-Configure-2-3](../../media/16734a98-31c4-4023-a2a5-10b7c95bc58e.png)
  
    若要确认每个删除，请再次选择 "**操作**" 列中的 "**删除**"。 
    
    ![Name-BP-Configure-2-4](../../media/409c21c5-51f4-4244-bb84-5d32084224b2.png)
  
    重复此两步操作，直到删除所有其他 MX 记录。
    
## <a name="add-the-cname-records-that-are-required-for-office-365"></a>添加 Office 365 所需的 CNAME 记录
<a name="BKMK_add_CNAME"> </a>

1. 若要开始，请使用[此链接](https://www.name.com/account/domain)转到 name.com 上你的域页面。系统将会提示你首先登录。
    
    ![Name-BP-Configure-1-1](../../media/1869b416-1d3f-4fb1-99c6-62b74ca7a4c7.png)
  
2. 在 **"我的域**" 下，选择要修改的域的名称。
    
    ![Name-BP-Configure-1-2](../../media/c8b96e1e-aa35-4fb1-8209-450f587fec4d.png)
  
3. 在 "**详细信息**" 列中，选择 " **DNS 记录**"。 
    
    ![Name-BP-Configure-1-3](../../media/c5da31e2-2f77-4d0c-b31d-189e6fb7b205.png)
  
4. 添加第一条 CNAME 记录。
    
    在新记录的框中，键入或复制并粘贴下表中第一行的值。
    
    （从下拉列表中选择" **类型**"值。） 
    
    |**类型**|**主机**|**应答**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |自动发现  <br/> |autodiscover.outlook.com  <br/> |使用默认值 (300)。  <br/> |
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com  <br/> |使用默认值 (300)。  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |使用默认值 (300)。  <br/> |
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |使用默认值 (300)。  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |使用默认值 (300)。  <br/> |
   
   ![Name-BP-Configure-3-1](../../media/4e34caaf-b418-40ec-abfa-fe62175a87c2.png)
  
5. 选择 "**添加记录**" 以添加第一条记录。 
    
    ![Name-BP-Configure-3-2](../../media/1053c2a7-07c3-4c1b-b54a-1c02881fb0ec.png)
  
6. 添加第二条 CNAME 记录。
    
    使用上表中第二行的值，然后选择 "**添加记录**" 以添加第二条记录。 
    
    按同样的方法，使用表中第 3 到 6 行的值添加其余记录。
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>为 SPF 添加 TXT 记录以帮助防止垃圾邮件
<a name="BKMK_add_TXT"> </a>

> [!IMPORTANT]
> 一个域所拥有的 SPF 的 TXT 记录不能超过一个。 如果域具有多个 SPF 记录，你将收到电子邮件错误，其中随附发送和垃圾邮件分类问题。 If you already have an SPF record for your domain, don't create a new one for Office 365. 可以将所需的 Office 365 添加到当前记录，这样就拥有包含两组值的*单个*SPF 记录。 
  
1. 若要开始，请使用[此链接](https://www.name.com/account/domain)转到 name.com 上你的域页面。系统将会提示你首先登录。
    
    ![Name-BP-Configure-1-1](../../media/1869b416-1d3f-4fb1-99c6-62b74ca7a4c7.png)
  
2. 在 **"我的域**" 下，选择要修改的域的名称。

    ![Name-BP-Configure-1-2](../../media/c8b96e1e-aa35-4fb1-8209-450f587fec4d.png)
  
3. 在 "**详细信息**" 列中，选择 " **DNS 记录**"。 
    
    ![Name-BP-Configure-1-3](../../media/c5da31e2-2f77-4d0c-b31d-189e6fb7b205.png)
  
4. 在新记录的框中，键入或复制并粘贴下表中的值。
    
    (Choose the **Type** value from the drop-down list.) 
    
    |**类型**|**主机**|**应答**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |(Leave this field empty.)  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **注意：** 建议复制粘贴此条目，以保证正确保留所有空格。           |Use the default value (300).  <br/> |
   
   ![Name-BP-Configure-4-1](../../media/cbbfc071-840a-4ffa-a59e-0dfce03063cc.png)
  
5. 选择 "**添加记录**"。
    
    ![Name-BP-Configure-4-2](../../media/db1e0e09-2b95-4fc1-88bd-e86da536921f.png)
  
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>添加 Office 365 所需的两条 SRV 记录
<a name="BKMK_add_SRV"> </a>

1. 若要开始，请使用[此链接](https://www.name.com/account/domain)转到 name.com 上你的域页面。系统将会提示你首先登录。
    
    ![Name-BP-Configure-1-1](../../media/1869b416-1d3f-4fb1-99c6-62b74ca7a4c7.png)
  
2. 在 **"我的域**" 下，选择要修改的域的名称。
    
    ![Name-BP-Configure-1-2](../../media/c8b96e1e-aa35-4fb1-8209-450f587fec4d.png)
  
3. 在 "**详细信息**" 列中，选择 " **DNS 记录 +**"。 
    
    ![Name-BP-Configure-1-3](../../media/c5da31e2-2f77-4d0c-b31d-189e6fb7b205.png)
  
4. 添加第一条 SRV 记录：
    
    在新记录的框中，键入或复制并粘贴下表中第一行的值。
    
    （从下拉列表中选择" **类型**"值。） 
    
    |**类型**|**服务**|**权重**|**TTL**|**优先级**|**协议**|**端口**|**目标**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV|sip|1|使用默认值 (300)。|100|tls|443|sipdir.online.lync.com <br> **注意：** 建议复制粘贴此条目，以保证正确保留所有空格。           |
    |SRV|sipfederationtls|1|使用默认值 (300)。|100|tcp|5061|sipfed.online.lync.com <br>**注意：** 建议复制粘贴此条目，以保证正确保留所有空格。           |
   
   ![Name-BP-Configure-5-1](../../media/d9a885fd-7300-45b6-ad4c-0b4bf1067560.png)
  
5. 选择 "**添加记录**"。

    ![Name-BP-Configure-5-2](../../media/a804d51d-8f57-4b0b-8bd6-a52eb1c87a97.png)
  
6. 添加第二条 SRV 记录：

使用上表中下一行的值，然后选择 "**添加记录**" 以添加第二条记录。

>[!NOTE]
>DNS 更改通常需要 15 分钟左右才能生效。 但是，有时可能需要更长时间，您所做的更改才会在 Internet 的 DNS 系统中更新。 如果添加 DNS 记录后遇到邮件流问题或其他问题，请参阅 [更改域名或 DNS 记录后出现的问题的疑难解答](../get-help-with-domains/find-and-fix-issues.md)。
