---
title: Office 365 ATP 中的 Campaigns Views
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: mcostea
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: 了解 Office 365 高级威胁防护中的 Campaigns Views。
ms.openlocfilehash: 40eab14dff8d0c51a35bfbc7a04365a5a025e207
ms.sourcegitcommit: 08a4ee7765f3eba42f0c037c5c564c581e45df3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "42637325"
---
# <a name="campaign-views-in-office-365-atp"></a>Office 365 ATP 中的 Campaign Views

Campaign Views 是 Office 365 安全与合规中心的高级威胁防护 (ATP) 中的一项功能，可以对服务中的钓鱼攻击进行识别和分类。 Campaign Views 可以帮助你：

- 高效调查和应对钓鱼攻击。

- 更好地了解攻击范围。

- 向决策者展示价值。

借助 Campaign Views，可以让你比任何人都更快获得有关攻击的更全面概览。

## <a name="what-is-a-campaign"></a>什么是活动 (campaign)？

活动是针对一个或多个组织的协同式电子邮件攻击。 窃取凭据和公司数据的电子邮件攻击是一个大型且 lucrative 的行业。 随着技术的提高而停止攻击的努力，攻击者将修改其方法以确保持续的成功。

Microsoft 利用整个 Office 365 服务中大量的防网络钓鱼、反垃圾邮件和反恶意软件数据来帮助确定市场活动。 我们根据几个因素对攻击信息进行分析和分类。 例如：

- **攻击来源**：源 IP 地址和发件人电子邮件域名。

- **攻击邮件属性**：攻击邮件的内容、样式和语气。

- **攻击收件人**：收件人域名、收件人工作职能（管理员、高管等）、公司类型（大型、小型、公共、私有等）和行业。

- **攻击负载**：攻击邮件中的恶意链接、附件或其他负载。

市场活动可能较短，或者可能跨多天、几周或月，且具有有效和非活动时段。 可能会针对你的特定组织发起市场活动，或你的组织可能是跨多个公司的更大市场活动的一部分。

## <a name="campaign-views-the-office-365-security--compliance-center"></a>Campaign Views Office 365 安全与合规中心

"活动" 视图在**威胁管理** \> **市场活动**的[安全性 & 合规性中心](https://protection.office.com)中提供。

![安全和合规中心中的活动概述](../../media/campaigns-overview.png)

您还可以从以下来源获取市场活动视图：

- **威胁管理** \> **资源管理器** \> **视图** \> **市场活动**

- **威胁管理** \> **资源管理器** \> **查看** \> **所有电子邮件** \> **活动**

> [!TIP]
> 如果看不到任何活动数据，请尝试更改日期范围。

“概述”页面显示有关该活动的以下信息：

- **名称**

- **示例主题**：活动中某封邮件的主题行。 请注意，市场活动中的所有邮件都不一定具有相同的主题。

- **类型**：当前，此值始终是**网络钓鱼**。

- **子类型**：此活动中作为钓鱼对象的品牌。 当通过 ATP 技术驱动检测时，会将前缀**ATP**添加到子类型值中。

- **收件人**：此活动所面向的用户数。

- **Inboxed**：在其收件箱中接收来自此市场活动的邮件的用户数（未传递给垃圾邮件）。

- **单击**：在网络钓鱼邮件中单击 URL 的用户数。

- **单击 "速率**：由 '**单击** / **Inboxed**' 计算的百分比。 此值是市场活动的有效性的指标，以及收件人是否能够将邮件标识为网络钓鱼并避免在有效负载 URL 上单击。

- 已**访问**：有多少用户实际将其通过到有效负载网站。 如果有**单击**的值，但安全链接阻止了对网站的访问，则此值将为零。

单击活动的名称时，活动详细信息将显示在浮出控件中。

## <a name="campaign-details"></a>活动详细信息

“活动详细信息”视图中提供了有关活动的大量信息：

- 活动信息：

  - **ID**：唯一的市场活动标识符。

  - **开始时间**和**结束时间**：你选择的日期范围筛选器。

  - **影响**：您选择的日期范围筛选器的以下数据：
  
    - 总收件人数。

    - "Inboxed" （即传递到 "收件箱"，而不是 "垃圾邮件"）的邮件数。

    - 在网络钓鱼邮件中单击 URL 有效负载的用户数。

    - Howe 许多用户访问了该 URL。

  - 活动的时间线：活动的开始时间和结束时间以及随时间推移的邮件数量。

### <a name="campaign-flow"></a>活动流

关于活动的重要详细信息显示在**流程**部分中的水平流程图表（称为 _Sankey_ 图表）中。 这些详细信息将帮助你了解活动的元素和组织中的潜在影响。

![不包含用户 URL 单击次数的活动详细信息](../../media/campaign-details-no-recipient-actions.png)

如果将鼠标悬停在图表中的水平带区上，则将看到相关邮件的数目（例如来自特定来源 IP 的邮件，使用指定发件人域名的来自来源 IP 的邮件等）。

此图表包含以下信息：

- **发件人 IP**

- **发件人域名**

- **筛选 verdicts**：此处的值与 "可用的网络钓鱼" 和 "垃圾邮件" 筛选 verdicts （如[反垃圾邮件邮件头](anti-spam-message-headers.md)中所述）相关。 下表描述了可用的值：

  |值|垃圾邮件筛选器判定|说明|
  |:-----|:-----|:-----|
  | **Allowed**|`SFV:SKN` <br/><br/> `SFV:SKI`|垃圾邮件筛选（例如，通过邮件流规则（也称为传输规则）进行评估之前，邮件被标记为非垃圾邮件和/或跳过的筛选器。<br/><br/>邮件因其他原因而跳过垃圾邮件筛选（例如，发件人和收件人似乎位于同一组织中）。|
  |**Blocked**|`SFV:SKS`|垃圾邮件筛选（例如，通过邮件流规则）评估邮件之前，邮件被标记为垃圾邮件。|
  |**已检测**|`SFV:SPM`|垃圾邮件筛选器将邮件标记为垃圾邮件。|
  |**未检测到**|`SFV:NSPM`|垃圾邮件筛选器将邮件标记为 "非垃圾邮件"。|
  |**以后**|`SFV:SKQ`|邮件跳过垃圾邮件筛选，因为它已从隔离区中释放。|
  |**租户允许**<sup>\*</sup>|`SFV:SKA`|邮件由于反垃圾邮件策略设置而跳过垃圾邮件筛选（例如，发件人位于 "允许的发件人" 列表或 "允许的域" 列表中）。|
  |**租户块**<sup>\*\*</sup>|`SFV:SKA`|由于反垃圾邮件策略设置（例如，发件人位于 "允许的发件人列表" 或 "允许的域" 列表中），垃圾邮件筛选阻止了邮件。|
  |**用户允许**<sup>\*</sup>|`SFV:SFE`|邮件跳过垃圾邮件筛选，因为发件人位于 Outlook 的用户安全发件人列表中。|
  |**用户块**<sup>\*\*</sup>|`SFV:BLK`|邮件被垃圾邮件筛选阻止，因为发件人位于 Outlook 中的用户阻止的发件人列表中。|
  |**ZAP**|不适用|[零小时自动清除（ZAP）](zero-hour-auto-purge.md)根据您的反垃圾邮件策略设置（移动到 "垃圾邮件" 文件夹或隔离的）对已发送邮件采取操作。|

  <sup>\*</sup>检查您的反垃圾邮件策略，因为服务可能阻止了允许的邮件。

  <sup>\*\*</sup>检查反垃圾邮件策略，因为应隔离但不传递这些邮件。

- **送达位置**：你希望调查发送到收件人的邮件（发送到收件箱或垃圾邮件文件夹），即使用户未单击邮件中的有效负载 URL。 您还可以从隔离区中删除隔离的邮件。 有关详细信息，请参阅[在 Office 365 中隔离电子邮件消息](quarantine-email-messages.md)。

  - **已删除文件夹**

  - **已**

  - **外部**：收件人位于你的内部部署电子邮件组织中。

  - **失败**

  - **哪个**

  - **收件箱**

  - **垃圾邮件文件夹**

  - **隔离**

  - **Unknown**

> [!NOTE]
> 在包含10个以上项目的所有层中，将显示前10个项目，而其余的项目捆绑在**一起。**

#### <a name="url-clicks"></a>URL 单击次数

将仿冒邮件传递给收件人（"收件箱" 或 "垃圾邮件" 文件夹）时，总是有用户单击有效负载 URL 的机会。 如果不单击已传递邮件中的 URL，则会使其成功，但您需要确定在第一个位置将仿冒邮件传递到其邮箱的原因。

如果用户单击了仿冒邮件中的有效负载 URL，则操作将显示在 "市场活动详细信息" 视图中关系图的 " **URL 单击**" 区域中。

- **Allowed**

- **BlockPage**：收件人单击了有效负载 URL，但组织中的[ATP 安全链接](atp-safe-links.md)策略阻止了其对恶意网站的访问。

- **BlockPageOverride**：收件人单击了邮件中的有效负载 URL 后，ATP 安全链接尝试停止它们，但允许它们替代该块。 您需要调查[安全链接策略](set-up-atp-safe-links-policies.md)，以了解为什么允许用户覆盖安全链接判定并继续进入恶意网站。

- **PendingDetonationPage**： ATP 安全附件在虚拟计算机环境中打开有效负载 URL 的过程，并查看发生的情况。

- **PendingDetonationPageOverride**：允许收件人重写有效负载沙箱进程并打开 URL，而不等待结果。

### <a name="tabs"></a>选项卡

“活动详细信息”视图中有多个选项卡，可用于进一步调查活动。

- **URL 单击**：如果用户未单击仿冒邮件中的有效负载 URL，则此部分将为空。 如果用户能够单击该 URL，则将填充以下值：

  - **用户**<sup>\*</sup>

  - **URL**<sup>\*</sup>

  - **单击时间**

  - **单击操作**

- **发件人 IP**

  - **发件人 IP**<sup>\*</sup>

  - **总计数**

  - **收件箱邮件计数**

  - **阻止的计数**

  - 已**通过的 SPF**：发件人[策略框架（SPF）](how-office-365-uses-spf-to-prevent-spoofing.md)对发件人进行身份验证。 未通过 SPF 验证的发件人表示发件人未经过身份验证，或者邮件正在哄骗合法发件人。

- **发件人**

  - **发件人**：这是 SMTP MAIL from 命令中的实际发件人地址，而不一定是用户在其电子邮件客户端中看到的 "发件人：" 电子邮件地址。

  - **总计数**

  - **Inboxed**

  - **不 Inboxed**

  - 已**通过 DKIM**：发件人由[识别为邮件的域密钥（DKIM）](support-for-validation-of-dkim-signed-messages.md)进行身份验证。 未通过 DKIM 验证的发件人表示发件人未经过身份验证，或者邮件正在哄骗合法的发件人。

  - 已**通过 DMARC**：发件人通过[基于域的邮件身份验证、报告和合规性（DMARC）](use-dmarc-to-validate-email.md)进行身份验证。 未通过 DMARC 验证的发件人表示发件人未经过身份验证，或者邮件正在哄骗合法的发件人。

- **有效负载**

  - **URL**<sup>\*</sup>

  - **总计数**

<sup>\*</sup> 单击此值将打开一个新浮出控件，其中包含有关“活动详细信息”视图顶部的指定项（用户、URL 等）的详细信息。 若要返回到“活动详细信息”视图，请单击新浮出控件中的“**完成**”。

### <a name="buttons"></a>按钮

通过“活动详细信息”视图中的按钮，可使用威胁资源管理器的强大功能进一步调查活动。

- **探索活动**：打开新的威胁资源管理器搜索选项卡，将**活动 ID** 值用作搜索筛选器。

- **浏览 Inboxed 消息**：使用**市场活动 ID**和送达位置打开新的威胁资源管理器搜索选项卡 **： "收件箱**" 作为搜索筛选器。
