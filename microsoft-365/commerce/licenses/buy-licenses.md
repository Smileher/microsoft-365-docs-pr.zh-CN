---
title: 管理订阅许可证
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- commerce
ms.custom:
- SaRA
- okr_SMB
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 36081d8d-b3fa-4948-8c34-e217bba825e1
description: 了解如何添加和删除 Office 365 for business 订阅的许可证。
ms.openlocfilehash: 2f9c6b58a478b18fa1844c33689a8a4974a5917a
ms.sourcegitcommit: 0d7d18b045c9a14c943bc382b16715e67c86259a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "42410039"
---
# <a name="manage-subscription-licenses"></a>管理订阅许可证

您可以使用这些步骤在订阅中添加或删除许可证。

不能删除订阅中已分配给用户的许可证。 如果要删除当前分配给某人的许可证，则需要先[删除用户的许可证](../../admin/manage/remove-licenses-from-users.md)，然后才能从订阅中删除该许可证。

::: moniker range="o365-worldwide"

> [!NOTE]
> 如果未使用新的 Microsoft 365 管理中心，可通过选择“**试用新的管理中心**”切换按钮（位于主页顶部）将其打开。

## <a name="what-you-need-to-know-about-buying-licenses-for-your-business-subscription"></a>你需要了解的有关为你的业务订阅购买许可证的相关信息

1. 在管理中心，转到“**账单**”\>“<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">产品和服务</a>”页面。

2. 在 "**产品 & 服务**" 页上，找到要向其添加或删除许可证的订阅，然后选择 "**添加/删除许可证**"。

    [如果看不到"添加/删除"链接，该怎么办？](#what-if-i-dont-see-the-addremove-licenses-link)

3. 在 "**许可证总数**" 框中，输入此订阅所需的许可证总数，然后选择 "**提交更改**"。 例如，如果有 100 个许可证并需要再添加 5 个，请输入 105。 如果要删除5个，请输入95。

购买新许可证后，请务必[将许可证分配给用户](../../admin/manage/assign-licenses-to-users.md)。

::: moniker-end

::: moniker range="o365-germany"

1. 在管理中心中，转到 "**记帐** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">订阅</a>" 页。

2. 在 "**订阅**" 页上，选择要向其添加或删除许可证的订阅，然后选择 "**添加/删除许可证**"。

    [如果看不到"添加/删除"链接，该怎么办？](#what-if-i-dont-see-the-addremove-licenses-link)

3. 在 "**许可证总数**" 框中，输入此订阅所需的许可证总数，然后选择 "**提交** \> **关闭**"。 例如，如果有 100 个许可证并需要再添加 5 个，请输入 105。 如果要删除5个，请输入95。

购买新许可证后，请务必[将许可证分配给用户](../../admin/manage/assign-licenses-to-users.md)。

::: moniker-end

::: moniker range="o365-21vianet"

1. 在管理中心中，转到 "**记帐** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">订阅</a>" 页。

2. 在 "**订阅**" 页上，选择要向其添加或删除许可证的订阅，然后选择 "**添加/删除许可证**"。

    [如果看不到"添加/删除"链接，该怎么办？](#what-if-i-dont-see-the-addremove-licenses-link)

3. 在 "**许可证总数**" 框中，输入此订阅所需的许可证总数，然后选择 "**提交** \> **关闭**"。 例如，如果有 100 个许可证并需要再添加 5 个，请输入 105。 如果要删除5个，请输入95。

购买新许可证后，请务必[将许可证分配给用户](../../admin/manage/assign-licenses-to-users.md)。

::: moniker-end

## <a name="what-if-i-dont-see-the-addremove-licenses-link"></a>如果看不到"添加/删除"链接，该怎么办？

此表介绍 "**添加/删除许可证**" 链接不可用的原因，以及您可以执行的操作。 

|Reason  |说明  |解决方案  |
|---------|---------|---------|
|正在等待信用检查。 |如果正在等待信用检查，你将看到"正在等待信用检查"消息，并在完成信用检查之后才能购买许可证。  | 稍后再次查看以查看是否已完成信用检查。 信用检查通常需要两个工作日才能完成。<br>完成信用检查后，应可在" **用户**"部分看到" **添加/删除许可证**"链接。 如果是这样，请转到[管理订阅许可证](#manage-subscription-licenses)。 |
|您使用产品密钥激活了订阅。| 如果订阅是使用 25 个字符的产品密钥购买并激活的，你将看到"预付费"字样。  |请参阅[向使用产品密钥支付的订阅添加许可证](add-licenses-using-product-key.md)。 |
|您通过合作伙伴购买了订阅。 | 如果订阅是通过合作伙伴购买的，你将看到"批量许可服务中心 (VLSC)"链接。 | 请参阅[向通过批量许可服务中心购买的订阅添加许可证](add-licenses-bought-through-vlsc.md)。 |
|您通过转销商购买了订阅。|| 如果订阅是通过云解决方案提供商 (CSP) 合作伙伴购买的，则必须联系该 CSP 合作伙伴以购买更多许可证。        |
|你有试用版订阅。 |试用版的 Office 365 将显示"试用版"字样。 | 必须先购买试用订阅，然后才能添加更多许可证。 请参阅[从免费试用版购买 Office 365 for business 订阅](../buy-a-subscription-from-your-free-trial.md)。|

## <a name="what-you-need-to-know-about-buying-licenses-for-your-business-subscription"></a>你需要了解的有关为你的业务订阅购买许可证的相关信息

### <a name="buying-licenses"></a>购买许可证

- 您必须是全局管理员或帐单管理员才能购买许可证。 有关详细信息，请参阅[关于管理员角色](../../admin/add-users/about-admin-roles.md)。
- 若要向订阅添加新用户且同时为其购买许可证，请参阅[向 Office 365 逐一或批量添加用户 - 管理员帮助](../../admin/add-users/add-users.md)。

### <a name="license-availability"></a>许可证可用性

- 如果通过信用卡或银行账户为订阅付费，则你购买的任何新许可证都将在收到订单确认后立即提供给你。 如果通过发票支付，可能必须等待完成信用检查才能使用新许可证。

  > [!NOTE]
  > 在某些国家或地区不提供按银行帐户付款。

- 如果你使用产品密钥预付订阅，你可以添加更多许可证，方法是添加信用卡或银行帐户，以涵盖新许可证的额外费用。 你购买新的许可证后，我们会添加第二个订阅，该订阅具有你刚才添加的新许可证的数量。 例如，如果你有一个订阅，该订阅具有 5 个许可证，然后你再购买了 10 个许可证，则会列出两个订阅：一个订阅具有 5 个预付的许可证，一个订阅具有 10 个新的许可证。

### <a name="billing-statements"></a>计费语句

- 如果通过信用卡或银行帐户支付，则购买新许可证的费用将在两天内出现在你的付款方式中。
- 如果通过结算清单支付，则购买新许可证的费用将显示在下一张帐单上。
- 如果在计费期间购买新许可证，则前一张帐单可能包含部分费用。应付余额将包含于下一张帐单。

## <a name="related-articles"></a>相关文章

[了解订阅和许可证](subscriptions-and-licenses.md)

[购买订阅的许可证](buy-licenses.md)

[购买另一个订阅](../buy-another-subscription.md)

[向用户分配许可证](../../admin/manage/assign-licenses-to-users.md)

[管理 Yammer 用户许可证](https://docs.microsoft.com/yammer/manage-yammer-users/manage-yammer-licenses-in-office-365)
