---
title: Office 365 邮件加密 FAQ
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/03/2019
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0432dce9-d9b6-4e73-8a13-4a932eb0081e
description: 有关 Office 365 中的新邮件保护功能如何工作的问题？ 在此处查找答案。
ms.openlocfilehash: 8d0b65ad60365154f8a35c5afe0b71b5a50d29a8
ms.sourcegitcommit: 93e6bf1b541e22129f8c443051375d0ef1374150
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "42634740"
---
# <a name="office-365-message-encryption-faq"></a>Office 365 邮件加密 FAQ

有关 Office 365 中的新邮件保护功能如何工作的问题？ 在此处查找答案。 此外，还请参阅 azure[信息保护中](https://docs.microsoft.com/information-protection/get-started/faqs-rms)有关数据保护的常见问题解答，以获取有关 Azure 信息保护中的数据保护服务、Azure 权限管理问题的答案。

## <a name="what-is-office-365-message-encryption-ome"></a>什么是 Office 365 邮件加密（OME）？

OME 将电子邮件加密和权限管理功能结合在一起。 权限管理功能由 Azure 信息保护提供支持。
  
## <a name="who-can-use-ome"></a>谁可以使用 OME？

在下列情况下，您可以使用 OME 的新功能：
  
- 如果您从未在 Office 365 中为 Exchange Online 设置 OME 或 IRM。

- 如果已设置 OME 和 IRM，则可以使用这些步骤（如果使用的是 azure 信息保护的 Azure 权限管理服务）。

- 如果您使用的是 Active Directory 权限管理服务（AD RMS）的 Exchange Online，则不能立即启用这些新功能。 相反，您需要先将[AD RMS 迁移到 Azure 信息保护](https://docs.microsoft.com/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)。 完成迁移后，您可以成功地设置 OME。

  如果你选择继续使用 Exchange Online 的本地 AD RMS，而不是迁移到 Azure 信息保护，你将无法使用这些新功能。

## <a name="what-subscriptions-do-i-need-to-use-the-new-ome-capabilities"></a>使用新的 OME 功能需要什么订阅？

若要使用新的 OME 功能，您需要以下计划之一：
  
- Office 365 邮件加密是作为 Office 365 企业版 E3 和 E5、Microsoft 企业版 E3 和 E5、Microsoft 365 Business、Office 365 A1、A3 和 A5 以及 Office 365 政府 G3 和 G5 的一部分提供的。 客户无需额外的许可证即可接收 Azure 信息保护支持的新保护功能。

- 您还可以将 Azure 信息保护计划1添加到以下计划，以接收新的 Office 365 邮件加密功能： Exchange Online 计划1、Exchange Online 计划2、Office 365 F1、Office 365 Business Essentials、Office 365 商业高级版或Office 365 企业版 E1。

- 每个用户从 Office 365 邮件加密中受益的人都需要获得功能的许可。

- 有关完整列表，请参阅[Exchange Online 服务说明](https://technet.microsoft.com/library/exchange-online-service-description.aspx)For the Office 365 邮件加密。

## <a name="can-i-use-exchange-online-with-bring-your-own-key-byok-in-azure-information-protection"></a>我是否可以使用 Exchange Online 在 Azure 信息保护中引入你自己的密钥（BYOK）？

是的！ Microsoft 建议您先完成设置 BYOK 的步骤，然后再设置 OME。
  
有关 BYOK 的详细信息，请参阅[规划和实现 Azure 信息保护租户密钥](https://docs.microsoft.com/information-protection/plan-design/plan-implement-tenant-key)。
  
## <a name="do-ome-and-byok-with-azure-information-protection-change-microsofts-approach-to-third-party-data-requests-such-as-subpoenas"></a>使用 Azure 信息保护执行 OME 和 BYOK 更改 Microsoft 对第三方数据请求（如 subpoenas）的方法？

否。 OME 以及提供和控制您自己的加密密钥（称为 BYOK）的选项不是为了响应执法 subpoenas 而设计的。 OME，BYOK for Azure 信息保护是针对以法规为重点的客户而设计的。 Microsoft 会对客户数据进行非常严重的第三方请求。 作为云服务提供商，我们始终提倡客户数据的隐私。 在我们获取传唤时，我们总是会尝试将第三方重定向到客户来获取信息。 （请阅读 Brad Smith 的博客：[保护客户数据免受政府窥探](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)）。 我们会定期发布我们收到的请求的详细信息。 有关第三方数据请求的详细信息，请参阅对[政府和执法版强制请求的响应，以访问](https://www.microsoft.com/trustcenter/privacy/govt-requests-for-data)Microsoft 信任中心上的客户数据。 此外，请参阅[在线服务条款（OST）](https://www.microsoft.com/Licensing/product-licensing/products.aspx)中的 "客户数据泄露"。
  
## <a name="how-is-this-feature-related-to-legacy-office-365-message-encryption-ome-and-information-rights-management-irm-features"></a>此功能与旧版 Office 365 邮件加密（OME）和信息权限管理（IRM）功能有何关系？

Office 365 邮件加密的新功能是现有 IRM 和旧版 OME 解决方案的演变。 下表提供了更多详细信息。
  
**旧版 OME、IRM 和新 OME 功能的比较**

|**功能**|**早期版本的 OME**|**IRM**|**新的 OME 功能**|
|:-----|:-----|:-----|:-----|
|**发送加密电子邮件**|仅通过 Exchange 邮件流规则|最终用户从 Outlook for Windows、Outlook for Mac 或 web 上的 Outlook 启动;或通过 Exchange 邮件流规则|最终用户从 Outlook for Windows、Outlook for Mac 或 web 上的 Outlook 启动;或通过邮件流规则|
|**版权管理**|-|"不要转发" 选项和自定义模板|"不要转发" 选项、"仅加密" 选项、"默认" 和 "自定义" 模板|
|**支持的收件人类型**|仅限外部收件人|仅限内部收件人|内部和外部收件人|
|**收件人体验**|外部收件人收到了他们在浏览器或下载的移动应用程序中下载和打开的 HTML 邮件。|内部收件人在 Outlook for Windows、Outlook for Mac 和 Outlook 网页版中仅收到加密电子邮件。|内部和外部收件人在 Outlook for Windows、Outlook for Mac、outlook 网页版、Outlook for Android 和 Outlook for iOS 中接收电子邮件，无论他们是否在同一 Office 365 组织中或在任何 Office 365 中，都可以通过 web 门户获取这些收件人。组织. OME 门户不需要单独下载。|
|**提供你自己的密钥支持**|不可用|不可用| 支持的 BYOK|

## <a name="how-do-i-enable-the-new-ome-capabilities-for-my-organization"></a>如何为我的组织启用新的 OME 功能？

请参阅[设置新的 Office 365 邮件加密功能](set-up-new-message-encryption-capabilities.md)。
  
## <a name="will-the-previous-version-of-ome-be-deprecated"></a>早期版本的 OME 是否已被弃用？

您仍可以使用 OME 的早期版本，它此时不会被弃用。 但是，我们强烈建议组织使用新的和改进的 OME 解决方案。 尚未部署 OME 的客户无法设置以前版本的 OME 的新部署。
  
## <a name="my-organization-uses-active-directory-rights-management-can-i-use-this-functionality"></a>我的组织使用 Active Directory 权限管理，我是否可以使用此功能？

否。 如果您使用的是 Active Directory 权限管理服务（AD RMS）的 Exchange Online，则不能立即启用这些新功能。 相反，您需要先将[AD RMS 迁移到 Azure 信息保护](https://docs.microsoft.com/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)。
  
## <a name="my-organization-has-an-exchange-hybrid-deployment-can-i-use-this-feature"></a>我的组织具有 Exchange 混合部署。 我是否可以使用此功能？

本地用户可以使用 Exchange Online 邮件流规则发送加密邮件。 若要执行此操作，您需要通过 Exchange Online 路由电子邮件。 有关详细信息，请参阅[第2部分：将邮件配置为从您的电子邮件服务器传递到 Office 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365)。
  
## <a name="what-email-client-do-i-need-to-use-in-order-to-create-an-ome-encrypted-message-what-applications-are-supported-for-sending-protected-messages"></a>需要使用什么电子邮件客户端才能创建 OME 加密邮件？ 发送受保护的邮件支持哪些应用程序？

您可以从 Outlook 2016、Outlook 2013 for Windows 和 Mac 以及 outlook 网页版中创建受保护的邮件。
  
## <a name="what-email-clients-are-supported-to-read-and-reply-to-protected-emails"></a>支持哪些电子邮件客户端读取和回复受保护的电子邮件？

Office 365 用户可以从 Outlook for Windows 和 Mac （2013和2016）、Outlook 网页版和 Outlook mobile （Android 和 iOS）读取和响应。 如果你的组织允许，你也可以使用 iOS 本机邮件客户端。 如果您是非 Office 365 用户，则可以通过 web 浏览器阅读并答复 web 上的加密邮件。
  
## <a name="what-file-types-are-supported-as-attachments-in-protected-emails-do-attachments-inherit-the-protection-policies-associated-with-protected-emails"></a>受保护的电子邮件中支持哪些文件类型作为附件？ 附件是否继承与受保护的电子邮件关联的保护策略？

你可以将任何文件类型附加到受保护的邮件，但仅对[此处](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide-file-types)提到的文件格式应用保护策略。
  
如果支持文件格式（如 Word、Excel 或 PowerPoint 文件），则始终保护文件，即使收件人已下载附件也是如此。 例如，如果附件受 "不转发" 保护，并且原始收件人下载并将附件转发给新的收件人，则新的收件人将无法打开受保护的文件。
  
## <a name="are-pdf-file-attachments-supported"></a>PDF 文件附件是否受支持？

是的！ 您可以为您的 Office 365 组织启用 PDF 附件加密。 若要对 PDF 附件启用加密，请在[Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)中运行以下命令：

```powershell
Set-IRMConfiguration -EnablePdfEncryption $true
```

PDF 加密使您能够通过安全通信或安全协作来保护敏感 PDF 文档。 对于所有 Outlook 客户端，邮件和未受保护的 PDF 附件都会继承 Exchange Online 中的数据丢失防护（DLP）策略或邮件流规则的 OME 保护。 此外，如果 web 用户上的 Outlook 附加了一个不受保护的 PDF 文档，并对邮件应用保护，邮件将继承邮件的保护。 用户只能在支持受保护的 Pdf 的应用程序中打开加密附件（例如，OME 门户和 Azure 信息保护查看器）。

  
## <a name="are-onedrive-for-business-attachments-supported"></a>OneDrive for business 附件是否受支持？

Not yet. OneDrive for business 附件不受支持，最终用户无法对包含云 OneDrive for Business 附件的邮件进行加密。
  
## <a name="what-email-clients-support-preview-of-encrypted-attachments-in-protected-emails"></a>哪些电子邮件客户端支持在受保护的电子邮件中预览加密附件？

当使用受保护的邮件保护附件时，Outlook 客户端可以提供对文档直接预览的功能。 Outlook 支持预览 Office 文档（.docx、.xlsx、.pptx、doc、xls、ppt）。 Web 上的 Outlook 支持 Office 文档（.docx、.xlsx、.pptx）和 PDF 的预览。  

## <a name="can-i-automatically-encrypt-messages-by-setting-up-policies"></a>是否可以通过设置策略自动加密邮件？

是。 使用 Exchange Online 中的邮件流规则，根据特定条件自动加密邮件。 例如，您可以创建基于收件人 ID、收件人域或邮件正文或主题中的内容的策略。 请参阅[定义邮件流规则以对 Office 365 中的电子邮件进行加密](define-mail-flow-rules-to-encrypt-email.md)。
  
## <a name="can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail"></a>是否可以自动删除传入和传出邮件的加密？

管理员可以设置邮件流规则，以删除传出邮件的加密。 无法设置规则以删除传入邮件的加密。

## <a name="can-i-automatically-encrypt-messages-by-setting-up-policies-in-data-loss-prevention-dlp-through-the-security-amp-compliance-center"></a>是否可以通过安全&amp;合规中心在数据丢失防护（DLP）中设置策略来自动加密邮件？

是的！ 您可以在 Exchange Online 中设置邮件流规则，也可以使用安全&amp;合规性中心中的 DLP 进行设置。
  
## <a name="can-i-customize-encrypted-messages-with-my-company-branding"></a>我是否可以使用我的公司品牌自定义加密邮件？

是的！ 有关自定义电子邮件和 OME 门户的信息，请参阅将组织的品牌添加到加密邮件。 请参阅[将组织的品牌添加到加密邮件](add-your-organization-brand-to-encrypted-messages.md)。
  
## <a name="are-there-any-reporting-capabilities-or-insights-for-encrypted-emails"></a>是否有任何报告功能或对加密电子邮件的见解？

安全与合规中心中有一个加密报告。 请参阅[在安全 & 合规中心中查看电子邮件安全报告](../security/office-365-security/view-email-security-reports.md)。
  
## <a name="can-i-use-message-encryption-with-compliance-features-such-as-ediscovery"></a>是否可以对合规性功能（如电子数据展示）使用邮件加密？

是。 所有加密的电子邮件都可通过 Office 365 合规性功能发现。

## <a name="can-i-remove-encryption-from-email"></a>是否可以从电子邮件中删除加密？

管理员可以设置邮件流规则，以从传出邮件中删除加密。 无法使用邮件流规则从传入邮件中删除加密。

## <a name="is-delegated-access-supported"></a>是否支持委派访问权限？

此时不作用。

## <a name="can-i-open-encrypted-messages-sent-to-a-shared-mailbox"></a>是否可以打开发送到共享邮箱的加密邮件？

是的！ 共享邮箱支持加密邮件。

- 用户可以在共享邮箱中打开受保护的邮件，其中共享邮箱作为通讯组的一部分收到受保护的邮件。

- 当用户使用 Outlook for Windows、Outlook for Mac 和 Outlook 网页版时，用户可以查看从电子邮件继承保护的附件。

下表列出了受支持的共享邮箱客户端。

| 平台 | 阅读邮件 | 查看电子邮件附件 |
|----------|-----------|------------------------|
| Outlook 网页版 | 是 | 是                |
| Outlook for Windows| 是 | 是                |
| Outlook for Mac    | 是 | 是                |
| Outlook for Android| 是 | 否                 |
| Outlook for iOS    | 是 | 否                 |
|

目前有两个已知的限制：

- 仅支持通过直接用户分配向共享邮箱提供的访问权限。 我们不支持通过启用电子邮件的安全组进行分配。

- 您不能使用 Outlook mobile 打开在移动设备上收到的电子邮件附件。
