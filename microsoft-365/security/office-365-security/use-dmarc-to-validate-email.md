---
title: 使用 DMARC 验证 Office 365 中的电子邮件
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 4a05898c-b8e4-4eab-bd70-ee912e349737
ms.collection:
- M365-security-compliance
description: 了解如何配置基于域的邮件身份验证、报告和一致性 (DMARC) 以验证从 Office 365 组织发送的邮件。
ms.openlocfilehash: 0702baec4dd2b585dcf45546befc19a6108004b9
ms.sourcegitcommit: 93e6bf1b541e22129f8c443051375d0ef1374150
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "42633430"
---
# <a name="use-dmarc-to-validate-email-in-office-365"></a>使用 DMARC 验证 Office 365 中的电子邮件

基于域的邮件身份验证、报告和一致性 ([DMARC](https://dmarc.org)) 与发件人策略框架 (SPF) 和域密钥识别邮件 (DKIM) 结合使用，以验证邮件发件人并确保目标电子邮件系统信任从你的域发送的邮件。 实现使用 SPF 和 DKIM 的 DMARC 可以针对欺骗和钓鱼电子邮件提供额外的保护。 DMARC 可帮助接收邮件系统确定如何处理从你的域发送且未通过 SPF 或 DKIM 检查的邮件。

> [!TIP]
> 请访问 [Microsoft 智能安全协会 (MISA)](https://www.microsoft.com/misapartnercatalog) 目录，查看哪些第三方供应商提供 Office 365 的 DMARC 报告。 

## <a name="how-do-spf-and-dmarc-work-together-to-protect-email-in-office-365"></a>SPF 和 DMARC 如何协同工作来保护 Office 365 中的电子邮件？
<a name="SPFandDMARC"> </a>

 电子邮件可能包含多个发送方、发件人或地址。这些地址用于不同用途。例如，以下列地址为例： 
  
- **“邮件发件人”地址**：标识发件人，并指定在传送邮件过程中出现任何问题（例如未送达通知）时发送返回通知的地址。 该地址出现在电子邮件的信封部分，而电子邮件应用程序通常不显示此地址。 有时称其为" 5321.MailFrom 地址"或"反向路径地址"。

- **“发件人”地址**：由邮件应用程序显示为发件人地址的地址。 此地址标识电子邮件的作者。 即，负责撰写邮件的个人或系统的邮箱。 有时也称其为"5322.From 地址"。

SPF 使用 DNS TXT 记录为给定的域提供获得授权的发送 IP 地址的列表。通常情况下，仅会针对 5321.MailFrom 地址执行 SPF 检查。这意味着，使用 SPF 本身时 5322.From 地址未通过身份验证。这样允许用户接收通过 SPF 检查但具有伪造的 5322.From 发件人地址的邮件。以下面的 SMTP 脚本为例：
  
```text
S: Helo woodgrovebank.com
S: Mail from: phish@phishing.contoso.com
S: Rcpt to: astobes@tailspintoys.com
S: data
S: To: "Andrew Stobes" <astobes@tailspintoys.com>
S: From: "Woodgrove Bank Security" <security@woodgrovebank.com>
S: Subject: Woodgrove Bank - Action required
S:
S: Greetings User,
S: 
S: We need to verify your banking details.
S: Please click the following link to verify that we have the right information for your account.
S: 
S: https://short.url/woodgrovebank/updateaccount/12-121.aspx
S:
S: Thank you,
S: Woodgrove Bank
S: .
```

在此脚本中，发件人地址如下所示：
  
- 邮件发件人地址 (5321.MailFrom)：phish@phishing.contoso.com

- 发件人地址 (5322.From)：security@woodgrovebank.com

如果你配置了 SPF，那么接收服务器针对从 phish@phishing.contoso.com 地址发送的邮件执行检查。如果该邮件来自 phishing.contoso.com 域的有效源，则会通过 SPF 检查。由于电子邮件客户端仅显示发件人地址，用户可以看到此邮件来自 security@woodgrovebank.com。单独使用 SPF，永远不会验证 woodgrovebank.com 的有效性。
  
使用 DMARC 时，接收服务器还会针对发件人地址执行检查。在上面的示例中，如果正好存在 woodgrovebank.com 的 DMARC TXT 记录，那么针对发件人地址的检查会失败。
  
## <a name="what-is-a-dmarc-txt-record"></a>什么是 DMARC TXT 记录？
<a name="WhatisDMARC"> </a>

像 SPF 的 DNS 记录一样，DMARC 的记录是一个 DNS 文本 (TXT) 记录，有助于防止欺骗和钓鱼。在 DNS 中发布 DMARC TXT 记录。DMARC TXT 记录根据发送域的可疑所有者来验证电子邮件作者的 IP 地址，从而验证电子邮件的来源。 DMARC TXT 记录可以标识得到授权的出站电子邮件服务器。然后，目标电子邮件系统可以验证接收的邮件是否来自得到授权的出站电子邮件服务器。
  
Microsoft 的 DMARC TXT 记录如下所示：
  
```text
_dmarc.microsoft.com.   3600    IN      TXT     "v=DMARC1; p=none; pct=100; rua=mailto:d@rua.agari.com; ruf=mailto:d@ruf.agari.com; fo=1" 
```

Microsoft 将其 DMARC 报告发送至 [Agari](https://agari.com)（第三方）。 Agari 收集并分析 DMARC 报告。 请访问 [MISA 目录](https://www.microsoft.com/misapartnercatalog)，查看有哪些更多的第三方供应商提供 Office 365 的 DMARC 报告。
  
## <a name="implement-dmarc-for-inbound-mail"></a>为入站邮件实现 DMARC
<a name="implementDMARCinbound"> </a>

你不必为在 Office 365 中收到的邮件设置 DMARC。我们已经为你处理好了一切。如果你想了解未通过我们的 DMARC 检查时如何处理邮件，请参阅 [Office 365 如何处理未通过 DMARC 检查的入站电子邮件](use-dmarc-to-validate-email.md#inbounddmarcfail)。
  
## <a name="implement-dmarc-for-outbound-mail-from-office-365"></a>从 Office 365 中为出站邮件实现 DMARC
<a name="implementDMARCoutbound"> </a>

如果使用 Office 365 但没有使用自定义域，即，使用 onmicrosoft.com，无需执行任何其他操作即可为组织配置或实现 DMARC。SPF 已为你和 Office 365 自动设置就绪，并为发送邮件生成 DKIM 签名。有关此签名的详细信息，请参阅 [DKIM 和 Office 365 的默认行为](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior)。
  
 如果有自定义域，或者除了 Office 365 以外还使用本地 Exchange 服务器，则需要为出站邮件手动实现 DMARC。可以通过以下步骤为自定义域实现 DMARC：
  
- [步骤 1：为域标识邮件的有效源](use-dmarc-to-validate-email.md#IdentifyValidSources)

- [步骤 2：在 Office 365 中为域设置 SPF](use-dmarc-to-validate-email.md#ConfigSPF)

- [步骤 3：在 Office 365 中为自定义域设置 DKIM](use-dmarc-to-validate-email.md#ConfigDKIM)

- [步骤 4：在 Office 365 中为域生成 DMARC TXT 记录](use-dmarc-to-validate-email.md#CreateDMARCRecord)

### <a name="step-1-identify-valid-sources-of-mail-for-your-domain"></a>步骤 1：为域标识邮件的有效源
<a name="IdentifyValidSources"> </a>

如果你已经设置了 SPF，那么你已经通过了本练习。但是，对于 DMARC，还有其他一些注意事项。为域标识邮件的源时需要回答以下两个问题：
  
- 哪些 IP 地址从我的域发送邮件？

- 对于第三方代表我发送的邮件，5321.MailFrom 和 5322.From 域会匹配吗？

### <a name="step-2-set-up-spf-for-your-domain-in-office-365"></a>步骤 2：在 Office 365 中为域设置 SPF
<a name="ConfigSPF"> </a>

既然你拥有了所有的有效发件人的列表，你可以按照步骤[Set up SPF in Office 365 to help prevent spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md)。
  
例如，假定 contoso.com 从 Exchange Online 中发送邮件，本地 Exchange 服务器的 IP 地址是 192.168.0.1，并且 Web 应用程序的 IP 地址是 192.168.100.100，则 SPF TXT 记录将如下所示：
  
```text
contoso.com  IN  TXT  " v=spf1 ip4:192.168.0.1 ip4:192.168.100.100 include:spf.protection.outlook.com -all"
```

作为最佳做法，请确保 SPF TXT 记录考虑第三方发件人。
  
### <a name="step-3-set-up-dkim-for-your-custom-domain-in-office-365"></a>步骤 3：在 Office 365 中为自定义域设置 DKIM
<a name="ConfigDKIM"> </a>

一旦设置了 SPF，就需要设置 DKIM。你可以使用 DKIM 将数字签名添加到电子邮件的邮件头中。如果你不设置 DKIM，反而允许 Office 365 对你的域使用默认的 DKIM 配置，则 DMARC 可能会失败。这是因为默认的 DKIM 配置使用你的初始 onmicrosoft.com 域作为 5322.From 地址，而不是使用自定义域。这将强制从你的域发送的所有电子邮件的 5321.MailFrom 和 5322.From 地址不匹配。
  
如果你有代表你发送邮件的第三方发件人，并且他们发送的邮件的 5321.MailFrom 和 5322.From 地址不匹配，则该电子邮件将无法通过 DMARC。若要避免此问题，你需要专门为具有该第三方发件人的域设置 DKIM。这将允许 Office 365 验证来自此第三方服务的电子邮件。 但是，它也允许其他方（例如，Yahoo、Gmail 和 Comcast）验证通过该第三方发送给他们的电子邮件，就好像电子邮件是由你发送的一样。这是有好处的，因为它允许你的客户构建对你的域的信任，无论他们的邮箱位于何处，与此同时，Office 365 不会因欺骗而将邮件标记为垃圾邮件，因为它通过了对你的域的身份验证检查。
  
有关为域设置 DKIM 的说明，包括如何为第三方发件人设置 DKIM，以便他们可以欺骗你的域，请参阅[使用 DKIM 在 Office 365 中验证从自定义域发送的出站电子邮件](use-dkim-to-validate-outbound-email.md)。
  
### <a name="step-4-form-the-dmarc-txt-record-for-your-domain-in-office-365"></a>步骤 4：在 Office 365 中为域生成 DMARC TXT 记录
<a name="CreateDMARCRecord"> </a>

尽管还有此处未提及的其他语法选项，但这些都是最常用于 Office 365 的选项。在 Office 365 中为域生成 DMARC TXT 记录，格式如下：
  
```text
_dmarc.domain  TTL  IN  TXT  "v=DMARC1; p=policy; pct=100"
```

其中：
  
- *域*是你想要保护的域。 默认情况下，该记录可保护从该域和所有子域发送的邮件。 例如，如果指定 \_dmarc.contoso.com，那么 DMARC 会保护从该域和所有子域（例如 housewares.contoso.com 或 plumbing.contoso.com）发送的邮件。

- *TTL* 应始终相当于一小时。用于 TTL 的单位可以为小时（1 小时）、分钟（60 分钟）或秒（3600 秒），具体取决于你的域的注册机构。

- pct=100** 表示此规则应该用于所有的电子邮件。

- *策略*指定 DMARC 失败时你希望接收服务器遵循的策略。你可以将策略设置为无、隔离或拒绝。

有关要使用的选项的信息，请熟悉[在 Office 365 中实现 DMARC 的最佳做法](use-dmarc-to-validate-email.md#DMARCbestpractices)中的概念。
  
示例：
  
- 策略设置为无
  
    ```text
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=none"
    ```

- 策略设置为隔离
  
    ```text
    _dmarc.contoso.com 3600 IN  TXT  "v=DMARC1; p=quarantine"
    ```

- 策略设置为拒绝
  
    ```text
    _dmarc.contoso.com  3600 IN  TXT  "v=DMARC1; p=reject"
    ```

生成记录后，你需要在你的域注册机构中更新记录。有关为 Office 365 将 DMARC TXT 记录添加到 DNS 记录的说明，请参阅[管理 DNS 记录时为 Office 365 创建 DNS 记录](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23)。
  
## <a name="best-practices-for-implementing-dmarc-in-office-365"></a>在 Office 365 中实现 DMARC 的最佳做法
<a name="DMARCbestpractices"> </a>

你可以逐渐实现 DMARC，而不会影响邮件流的其余部分。创建和实施遵循以下步骤的推广计划。首先使用任一子域执行以下每一个步骤，然后使用其他子域，最后使用组织内的顶级域，然后再继续下一步骤。
  
1. 监视实现 DMARC 的影响

    从请求 DMARC 接收器向你发送关于使用该域时看到的消息的统计信息的子域或域的简单的监视模式记录开始。监视模式记录是将策略设置为无 (p=none) 的 DMARC TXT 记录。许多公司发布了 p=none 的 DMARC TXT 记录，因为他们不确定通过发布更严格的 DMARC 策略可能会丢失多少电子邮件。 

    即使在邮件传递基础结构中实现 SPF 或 DKIM 之前，你也可以这样做。但是，你将无法使用 DMARC 有效地隔离或拒绝邮件，直到你也实现了 SPF 和 DKIM 之后才可以。当引入 SPF 和 DKIM 时，通过 DMARC 生成的报告将提供通过这些检查和未通过检查的邮件的数量和源。你可以轻松地查看这些邮件占用了多少合法通信量，并解决所有问题。你还将开始看到即将发送的欺诈邮件的数量以及发送地点。

2. 请求外部邮件系统隔离未通过 DMARC 的邮件

    当你相信全部或大部分合法通信受 SPF 和 DKIM 保护，并且了解实现 DMARC 的影响时，你可以实施隔离策略。隔离策略是策略设置为隔离 (p=quarantine) 的 DMARC TXT 记录。通过执行此操作，你将要求 DMARC 接收器将来自你的域的未通过 DMARC 的邮件放入相当于垃圾邮件文件夹的本地位置，而不是客户的收件箱。

3. 请求外部邮件系统不接受未通过 DMARC 的邮件

    最后一步是实施拒绝策略。拒绝策略是策略设置为拒绝 (p=reject) 的 DMARC TXT 记录。执行此操作时，你将要求 DMARC 接收器不接受未通过 DMARC 检查的邮件。 

## <a name="how-office-365-handles-outbound-email-that-fails-dmarc"></a>Office 365 如何处理未通过 DMARC 的出站电子邮件
<a name="outbounddmarcfail"> </a>

如果邮件是从 Office 365 出站的而且未通过 DMARC，并且你已将策略设置为 p=quarantine 或 p=reject，则该邮件通过[出站邮件的高风险传递池](high-risk-delivery-pool-for-outbound-messages.md)进行路由。 出站电子邮件不存在任何替代方法。
  
如果你发布 DMARC 拒绝策略 (p=reject)，则 Office 365 中的任何其他客户都无法欺骗你的域，因为通过服务中继出站邮件时邮件将无法通过你的域的 SPF 或 DKIM。 不过，如果你发布 DMARC 拒绝策略，但并非所有电子邮件均通过 Office 365 进行了验证，部分可能会被标记为入站电子邮件的垃圾邮件（如上所述），或者如果你不发布 SPF 且尝试通过服务将其中继到出站，邮件将被拒绝。 例如，当你生成 DMARC TXT 记录时，如果你忘记包括代表你的域发送邮件的服务器和应用的某些 IP 地址，就会出现这种情况。
  
## <a name="how-office-365-handles-inbound-email-that-fails-dmarc"></a>Office 365 如何处理未通过 DMARC 的入站电子邮件
<a name="inbounddmarcfail"> </a>

如果发送服务器的 DMARC 策略是 p=reject，则 EOP 会将该邮件标记为垃圾邮件，而不是拒绝它。换句话说，对于入站电子邮件，Office 365 将 p=reject 和 p=quarantine 视为相同方式。
  
之所以像这样配置 office 365，是因为某些合法的电子邮件可能会无法通过 DMARC。例如，如果将邮件发送到一个邮件列表，然后将其中继到所有列表参与者，则该邮件可能无法通过 DMARC。如果 Office 365 拒绝这些邮件，人们可能会丢失合法的电子邮件，而且无法进行检索。 相反，这些邮件仍然无法通过 DMARC，但会将其标记为垃圾邮件而不是拒绝。如果需要，用户仍可以在其收件箱中获得这些邮件，方法如下：
  
- 用户使用其电子邮件客户端分别添加安全发件人

- 管理员创建一个适用于所有用户的 Exchange 邮件流规则（也称为传输规则），允许那些特定发件人的邮件。 

## <a name="how-office-365-utilizes-authenticated-received-chain-arc"></a>Office 365 如何使用经过身份验证的接收链 (ARC)
<a name="ARC"> </a>

Office 365 中的所有托管邮箱都将获得 ARC 的优势，实现改进的邮件可传递性和增强的反欺骗保护。 当电子邮件从始发服务器路由到收件人邮箱时，ARC 将保留来自所有参与中介或跃点的电子邮件身份验证结果。 在采用 ARC 之前，电子邮件路由中的中介执行的修改（如转发规则或自动签名）可能会在电子邮件到达收件人邮箱时导致 DMARC 故障。 有了 ARC 之后，身份验证结果的加密保留使得 Office 365 能够验证电子邮件发件人的真伪。 

目前，当 Microsoft 是 ARC 保护方时，Office 365 会利用 ARC 来验证身份验证结果，但计划在将来添加对第三方 ARC 保护方的支持。 

## <a name="troubleshooting-your-dmarc-implementation"></a>DMARC 实现疑难解答
<a name="dmarctroubleshoot"> </a>

如果你已配置了域的 MX 记录，其中 EOP 不是第一项，将不会为你的域强制执行 DMARC 失败。 
  
如果你是 Office 365 客户，并且你的域的主 MX 记录不指向 EOP，你将不会获得 DMARC 的好处。例如，如果你将 MX 记录指向你的本地邮件服务器，然后使用连接器将电子邮件路由到 EOP，则 DMARC 将不起作用。在这种情况下，接收域是一个接受的域，但 EOP 不是主 MX。例如，假设 contoso.com 本身指向其 MX 并将 EOP 用作辅助 MX 记录，contoso.com 的 MX 记录将如下所示：
  
```text
contoso.com     3600   IN  MX  0  mail.contoso.com
contoso.com     3600   IN  MX  10 contoso-com.mail.protection.outlook.com
```

由于它是主 MX，全部或大部分电子邮件将首先被路由到 mail.contoso.com，然后将邮件路由到 EOP。 在某些情况下，你甚至不可能将 EOP 列为 MX 记录，并直接挂接连接器来路由你的电子邮件。 EOP 不必是执行 DMARC 验证的第一个条目。 它只是确保验证，因为我们不能确定所有本地/非 O365 服务器都将执行 DMARC 检查。  设置 DMARC TXT 记录时，可以对客户的域（而不是服务器）强制执行 DMARC，但是实际上强制执行取决于接收服务器。  如果将 EOP 设置为接收服务器，那么 EOP 强制执行 DMARC。
  
## <a name="for-more-information"></a>更多详细信息
<a name="sectionSection8"> </a>

想要了解有关 DMARC 的详细信息？以下资源可以派上用场。
  
- [反垃圾邮件邮件头](anti-spam-message-headers.md) 包括 Office 365 执行 DMARC 检查时使用的语法和标头字段。 

- 参加 M[3](https://www.m3aawg.org/activities/training/dmarc-training-series)AAWG（消息、恶意软件、移动反滥用工作组）提供的 <sup>DMARC 培训系列</sup>。

- 使用检查表，位于 [dmarcian](https://space.dmarcian.com/deployment/)。

- 直接访问源，位于 [DMARC.org](https://dmarc.org)。

## <a name="see-also"></a>另请参阅
<a name="sectionSection8"> </a>

[Office 365 如何使用发件人策略框架 (SPF) 来防止欺骗](how-office-365-uses-spf-to-prevent-spoofing.md)
  
[在 Office 365 中设置 SPF 以防止欺骗](set-up-spf-in-office-365-to-help-prevent-spoofing.md)
  
[使用 DKIM 在 Office 365 中验证从自定义域发送的出站电子邮件](use-dkim-to-validate-outbound-email.md)
