---
title: Office 365 ATP 安全链接的工作原理
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: "\"安全链接\" 功能可提供对 Office 文档中的超链接和电子邮件中的超链接的单击时间验证。 阅读本文，了解 ATP 安全链接的工作原理。"
ms.openlocfilehash: c87eef2afbb3a694d9906de0c6c43bfeb576782b
ms.sourcegitcommit: 93e6bf1b541e22129f8c443051375d0ef1374150
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "42633970"
---
# <a name="how-office-365-atp-safe-links-works"></a>Office 365 ATP 安全链接的工作原理
> [!IMPORTANT] 
> 为了使 Office 365 ATP 安全链接正常运行，所有 Office 365 服务都必须在同一版本中。
         
## <a name="how-atp-safe-links-works-with-urls-in-email"></a>ATP 安全链接如何处理电子邮件中的 Url

从较高的层次来看， [ATP 安全链接](atp-safe-links.md)保护对电子邮件中的 url 的工作方式（托管在 Office 365 中，而不是在本地中）：
  
1. 用户接收包含 Url 的电子邮件。
    
2. 所有电子邮件都通过 Exchange Online 保护，其中应用了 internet 协议（IP）和信封筛选器、基于签名的恶意软件保护、反垃圾邮件和反恶意软件筛选器。 
    
3. 电子邮件到达用户的收件箱。
    
4. 用户登录到 Office 365，并转到其电子邮件收件箱。
    
5. 用户打开一封电子邮件，然后单击电子邮件中的 URL。
    
6. ATP 安全链接功能将在打开网站之前立即检查 URL。 该 URL 被标识为 "阻止"、"恶意" 或 "安全"。
        
   - 如果 URL 指向的网站包含在组织的[自定义阻止 url 列表](set-up-a-custom-blocked-urls-list-wtih-atp.md)中，则会打开一个[警告页面](atp-safe-links-warning-pages.md)。 
    
   - 如果 URL 指向已确定为恶意的网站，将打开 "[警告" 页](atp-safe-links-warning-pages.md)。 
    
   - 如果 URL 转到一个可下载的文件，并且您的组织的[ATP 安全链接策略](set-up-atp-safe-links-policies.md)已配置为扫描此类内容，则会检查下载的文件。 
    
   - 如果确定该 URL 是安全的，则会打开该网站。
    
## <a name="how-atp-safe-links-works-with-urls-in-office-documents"></a>ATP 安全链接如何处理 Office 文档中的 Url 

在较高级别，以下是[ATP 安全链接](atp-safe-links.md)保护对 Office 365 专业增强版或商业高级应用程序中的 url 的工作方式（Windows、Mac 上的 Word、Excel 和 PowerPoint 的当前版本、在 IOS 或 Android 设备上的 office 应用、Visio 在 Windows 中、在浏览器中为 OneNote）：
  
1. 用户已在其计算机、智能手机或平板电脑上安装 Office 365 专业增强版或商业高级版。 （或者，他们在浏览器中使用 Office。）
    
2. 用户打开 Word、Excel、PowerPoint、OneNote （在浏览器中）或 Visio （在桌面上），并使用其工作或学校帐户登录到 Office 365 企业版。 文档包含 Url。
    
3. 当用户单击文档中的某个 URL 时，ATP 安全链接服务将检查该链接。
    
   - 如果 URL 指向的网站包含在组织的[自定义阻止 url 列表](set-up-a-custom-blocked-urls-list-wtih-atp.md)中，则会向用户提供一个[警告页面](atp-safe-links-warning-pages.md)。
    
   - 如果 URL 指向已确定为恶意的网站，则会向用户提供[警告页面](atp-safe-links-warning-pages.md)。
    
   - 如果 URL 转到可下载的文件，并且已将[ATP 安全链接策略](set-up-atp-safe-links-policies.md)配置为扫描此类下载，则会检查可下载的文件。 
    
   - 如果该 URL 被认为是安全的，则会将用户转到该网站。
      
   - 如果 URL 检查失败，安全链接的保护将不会触发。 在桌面客户端上，将在继续进入网站之前警告用户。
      
> [!NOTE]
> 在每个会话开始时可能需要几秒钟的时间来验证用户是否已启用 Office 的 ATP 安全链接。 
      
