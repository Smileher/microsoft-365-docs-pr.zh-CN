---
title: 设置 Office 365 ATP 反网络钓鱼策略
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 08/29/2019
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 5a6f2d7f-d998-4f31-b4f5-f7cbf6f38578
ms.collection:
- M365-security-compliance
description: 在 office 365 Exchange Online Protection 的 Office 365 高级威胁防护和基本保护中具有全面保护的反网络钓鱼保护，可帮助保护您的组织免受基于模拟的恶意网络钓鱼攻击和其他网络钓鱼攻击。
ms.openlocfilehash: cc9c8ec0aa819696f3c53cff690be40ae82009fb
ms.sourcegitcommit: 21338a9287017a66298e0ff557e80051946ebf13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2020
ms.locfileid: "42604069"
---
# <a name="set-up-office-365-atp-anti-phishing-and-anti-phishing-policies"></a>设置 Office 365 ATP 反网络钓鱼和反网络钓鱼策略

[ATP 反网络钓鱼保护](atp-anti-phishing.md)是[Office 365 高级威胁防护](office-365-atp.md)的一部分，可帮助保护您的组织免受基于恶意模拟的网络钓鱼攻击和其他网络钓鱼攻击。 如果您是 Office 365 企业全局管理员或安全管理员，则可以设置 ATP 反网络钓鱼策略。

网络钓鱼攻击采用来自基于商品的攻击的各种形式，以供目标 spear 网络钓鱼或 whaling。 随着复杂程度的增加，甚至很难确定其中一些复杂的攻击。 幸运的是，Office 365 高级威胁防护可能会有所帮助。 您可以设置 ATP 反网络钓鱼策略，以帮助确保您的组织受到此类攻击的保护。

> [!NOTE]
> ATP 反网络钓鱼仅在高级威胁防护（ATP）中可用。 ATP 包含在订阅中，例如[microsoft 365 企业版](https://www.microsoft.com/microsoft-365/enterprise/home)、 [Microsoft 365 商业](https://www.microsoft.com/microsoft-365/business)版、Office 365 企业版 E5、Office 365 教育版 A5 等。如果您的组织有一个不包含 Office 365 ATP 的 Office 365 订阅，则可能会将 ATP 作为加载项进行购买。 有关详细信息，请参阅[office 365 高级威胁防护计划和定价](https://products.office.com/exchange/advance-threat-protection)和[Office 365 高级威胁防护服务说明](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)。 确保您的组织在 Windows 上使用最新版本的 Office 365 专业增强版，以充分利用 ATP 反钓鱼保护。

反网络钓鱼策略也可用于 Office 365 Exchange Online Protection，这是一组有限的反欺骗保护，旨在防止基于身份验证的攻击和基于 deception 的攻击。

要执行的操作：

1. 查看先决条件。

2. 了解反网络钓鱼和 ATP 反网络钓鱼策略选项。

3. 设置反网络钓鱼策略或 ATP 反网络钓鱼策略。

> [!IMPORTANT]
> 若要了解如何应用多种技术，请参阅在[您的电子邮件上运行多个保护方法和检测扫描时应用什么策略](how-policies-and-protections-are-combined.md)。

## <a name="review-the-prerequisites"></a>查看先决条件

- 若要定义（或编辑） ATP 策略，必须为您分配适当的角色。 下表介绍了一些示例：

  |角色|分配的位置/方式|
  |---------|---------|
  |Office 365 全局管理员|默认情况下，注册购买 Office 365 的人是全局管理员。 （请参阅[关于 Office 365 管理员角色](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)以了解详细信息。）|
  |安全管理员|Azure Active Directory 管理中心（[https://aad.portal.azure.com](https://aad.portal.azure.com)）|
  |Exchange Online 组织管理|Exchange 管理中心（[https://outlook.office365.com/ecp](https://outlook.office365.com/ecp)） <br>或 <br>  PowerShell cmdlet （请参阅[Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell)）|

  若要了解有关角色和权限的详细信息，请参阅[Office 365 &amp;安全合规中心中的权限](permissions-in-the-security-and-compliance-center.md)。

- 你可能会为你的组织设置多个反网络钓鱼策略。 Office 365 按照安全&amp;合规性中心中的 "**反仿冒页面**" 和 " **ATP 反网络钓鱼**" 页面上列出的顺序强制实施这些策略。 查看[策略选项](#learn-about-atp-anti-phishing-policy-options)之后，请花些时间来确定所需的策略数以及每个策略的优先级。

- 计划花大约5-15 分钟来设置第一次反网络钓鱼策略。

- 最长允许30分钟，新的或更新的策略将传播到所有的 Office 365 数据中心。

## <a name="set-up-an-anti-phishing-or-atp-anti-phishing-policy"></a>设置反网络钓鱼或 ATP 反网络钓鱼策略

Office 365 中的每个组织都有一个适用于所有用户的默认反网络钓鱼策略。 您可以创建多个自定义反网络钓鱼策略，您可以将其限定为组织中的特定用户、组或域。 您创建的自定义策略优先于默认策略。 您可以在 Office 365 安全&amp;合规中心中添加、编辑和删除反网络钓鱼策略。

1. 转到[https://protection.office.com](https://protection.office.com)并使用你的工作或学校帐户登录。

2. 在 "Office 365 安全&amp;合规中心" 的左侧导航窗格中的 "**威胁管理**" 下，选择 "**策略**"。

3. 在 "**策略**" 页上，选择 "**反网络钓鱼**" 或 " **ATP 反网络钓鱼**"。

4. 在 "**反钓鱼**或**ATP 反钓鱼诈骗**" 页面上，执行下列操作之一：

   - 若要添加新策略，请选择 " **+ 创建**"。

   - 若要编辑现有策略，请从 "**反网络钓鱼**" 页上显示的列表中选择策略名称。 （或者，您可以或选择列表上方的 "**默认策略**"。）在出现的页面上，选择 "**编辑策略**"。

5. 指定策略的名称、说明和设置。 有关详细信息，请参阅[了解 ATP 反网络钓鱼策略选项](#learn-about-atp-anti-phishing-policy-options)。

6. 查看设置后，选择 "**创建此策略**" （或 "**保存**"）。

## <a name="learn-about-atp-anti-phishing-policy-options"></a>了解 ATP 反网络钓鱼策略选项

当您设置或编辑 ATP 反网络钓鱼策略时，您可以从提供最完善和全面保护的多个选项中进行选择，如下表所述：

|**此设置**|**执行的操作**|**在需要执行以下操作时使用：**|
|:-----|:-----|:-----|
|**添加要保护的用户**|定义将受策略保护的电子邮件地址。 您可以添加最高为60的内部和外部地址，以防止其被模拟。|当您想要确保来自组织外部的邮件不会模拟正在保护的用户列表中的某个用户。 您可能想要保护的用户的示例有高级执行官、业务所有者、外部董事会成员等。  <br/> 此受保护的用户列表不同于策略应用于的人员列表，或者是为其强制实施策略的人员列表。 可以在 "策略选项" 的 "**应用**于" 部分中定义 "应用于" 列表。  <br/> 例如，如果添加`Mary Smith <marys@contoso.com>`为 "要保护的用户"，则将该策略应用于 "所有用户" 组。 这将确保该策略对显示为模拟 "Mary" 的邮件发送到 "所有用户" 组中的用户。|
|**添加要保护的域**|允许您从模拟中选择要保护的域。 您可以指定策略包括所有自定义域、以逗号分隔的域列表或两者的组合。 如果选择 "**自动包含我拥有的域**"，并且后来将域添加到 Office 365 组织中，则新域的此反网络钓鱼策略将会生效。|无论您何时想要确保来自组织外部的邮件不会模拟您的已验证域列表中定义的某个域或合作伙伴域的域。|
|**选择操作**|选择当 Office 365 检测到对添加到策略中的用户和域的模拟尝试时要采取的操作。 您可以为相同的反网络钓鱼策略中的用户和域选择不同的操作。 这些操作适用于已由 Office 365 标识的任何传入电子邮件，以模拟受此反网络钓鱼策略保护的用户帐户或域。  <br/> **隔离邮件**将电子邮件发送到 Office 365 隔离。 如果选择此选项，则不会将电子邮件发送给原始收件人。  <br/> **将邮件重定向到另一个电子邮件地址**电子邮件将发送到您指定的电子邮件地址。 您可以指定多个电子邮件地址。 如果选择此选项，则不会将电子邮件发送给原始收件人。  <br/> **将邮件移到收件人的 "垃圾邮件" 文件夹**将电子邮件发送到收件人的 "垃圾邮件" 文件夹。 选择此选项时，仍会将电子邮件发送给原始收件人，但不会将其放在收件人的收件箱中。  <br/> **传递邮件并向 "密件抄送" 行添加其他地址**电子邮件将传递给原始收件人。 此外，在邮件传递之前，您标识的用户将添加到邮件的 "密件抄送" 行。 选择此选项时，仍会将电子邮件发送到原始收件人的收件箱。  <br/> **不应用任何操作**将电子邮件传递到原始收件人的收件箱。 不会对电子邮件执行其他任何操作。  <br/> **启用网络钓鱼防护提示**在电子邮件中启用反网络钓鱼安全提示。|当您希望对 Office 365 已确定为在策略中定义的用户或域的模拟的邮件执行操作时。|
|**启用邮箱智能**|为此策略启用或禁用邮箱智能。 您只能为基于云的帐户启用邮箱智能，即，其邮箱完全托管在 Office 365 中的帐户。| 此功能使用机器学习来确定用户的电子邮件模式及其联系人。 使用此信息，AI 可以更好地区分正版和仿冒电子邮件。|
|**启用基于邮箱智能的模拟保护**|为此策略启用或禁用用于模拟保护的邮箱智能。 下面的重要方面是对给定邮箱的模拟的控制。|当您想要为基于每个用户的单个发件人地图的用户增强模拟结果时。 此智能允许 Office 365 自定义用户模拟检测，并更好地处理误报。 检测到用户模拟时，根据邮箱智能，可以定义对邮件执行的操作。|
|**添加受信任的发件人和域**|定义不会被此策略视为模拟的电子邮件地址和域。 来自作为受信任的发件人和域添加的发件人电子邮件地址和域中的邮件不会被分类为基于模拟的攻击。 因此，此策略中的操作和设置不会应用于来自这些发件人和域的邮件。  <br/><br/>这些列表的最大限制约为1000个条目。|当用户与触发模拟但被视为安全的域或用户进行交互时。 例如，如果合作伙伴与列表中定义的用户具有相同/类似的显示名称或域名。|
|**应用于**|定义其传入电子邮件将受策略规则制约的收件人。 您可以为与该策略相关联的收件人创建条件和例外。  <br/> 例如，您可以通过将规则应用于域中的所有收件人来为您的组织创建全局策略。  <br/> 您还可以创建例外规则，如不扫描特定收件人组的电子邮件的规则。|每个策略都必须与一组用户（例如，特定组或域中的用户）相关联。|
|**高级网络钓鱼阈值**|定义处理网络钓鱼邮件的方式的设置级别。  <br/> **Standard**：怀疑是电子邮件网络钓鱼的电子邮件是按标准方式处理的。  <br/> **主动**：系统处理怀疑是网络钓鱼的电子邮件，这与怀疑具有很高可信度的人的方法相同。  <br/> **更主动**：系统处理怀疑为网络钓鱼的电子邮件，就像怀疑具有很高可信度的人一样。  <br/> **最主动**：系统处理可疑的电子邮件，即具有较低、中或高度可信度的电子邮件，其方式与怀疑具有较高可信度的人一样。|当您希望更积极地处理 Office 365 中可能存在的网络钓鱼邮件时。 例如，具有较高的网络钓鱼的邮件将会对其执行最严格的操作，而概率较低的邮件则对其执行的操作较少。 此设置还会影响合并信号的筛选系统的其他部分。 这并不一定意味着会实现不同的操作。  实际上，您设置邮件网络钓鱼邮件的概率，以确定（相同）指定的操作。 随着设置级别的增加，移动好邮件的可能性也会增加。|

## <a name="learn-about-anti-phishing-policy-options"></a>了解反网络钓鱼策略选项

在设置或编辑反网络钓鱼时，可以从多个选项中进行选择，如下表所述：

|**此设置**|**执行的操作**|**在需要执行以下操作时使用：**|
|:-----|:-----|:-----|
|**应用于**|定义其传入电子邮件将受策略规则制约的收件人。 您可以为与该策略相关联的收件人创建条件和例外。  <br/> 例如，您可以通过将规则应用于域中的所有收件人来为您的组织创建全局策略。  <br/> 您还可以创建例外规则，如不扫描特定收件人组的电子邮件的规则。|每个策略都必须与一组用户（例如，特定组或域中的用户）相关联。|
|**选择操作**|选择当 Office 365 检测到组织内部或外部组织的欺骗尝试时要采取的操作。 这些操作适用于由 Office 365 标识的任何传入电子邮件，作为对此反网络钓鱼策略进行保护的用户的欺骗尝试。  <br/> **隔离邮件**将电子邮件发送到 Office 365 隔离。 如果选择此选项，则不会将电子邮件发送给原始收件人。  <br/> **将邮件移到收件人的 "垃圾邮件" 文件夹**将电子邮件发送到收件人的 "垃圾邮件" 文件夹。 选择此选项时，仍会将电子邮件发送给原始收件人，但不会将其放在收件人的收件箱中。  <br/> **不应用任何操作**将电子邮件传递到原始收件人的收件箱。 不会对电子邮件执行其他任何操作。|当您希望对 Office 365 已确定为在策略中定义的内部或外部域进行欺骗性尝试时对邮件执行操作时。|

在组织设置了反网络钓鱼策略或 ATP 反网络钓鱼策略之后，可以[查看高级威胁防护报告，以](view-reports-for-atp.md)了解服务的工作方式。

## <a name="example-anti-phishing-policy-to-protect-a-user-and-a-domain"></a>示例：保护用户和域的反网络钓鱼策略

本示例将设置名为 "Domain 和 CEO" 的策略，该策略提供模拟的用户和域保护，然后将该策略应用于域`contoso.com`中用户接收的所有电子邮件。 安全管理员已确定策略必须满足以下业务要求：

- 策略需要为 CEO 的电子邮件帐户和整个域提供保护。

- 确定为对 CEO 的用户帐户进行模拟尝试的邮件需要重定向到安全管理员的电子邮件地址。

- 确定为对域进行模拟尝试的邮件不太紧急，应进行隔离，以便日后复查。

Contoso 的安全管理员可能会使用如下所示的值，以便创建满足这些需求的反网络钓鱼策略。

|||
|:-----|:-----|
|**设置或选项**|**示例**|
|名称|域和 CEO|
|说明|确保未模拟 CEO 和我们的域。|
|添加要保护的用户|CEO 的电子邮件地址（最小值）。|
|添加要保护的域|包含 CEO 的办公室的组织域。|
|选择操作|如果模拟用户发送电子邮件：选择 "**将邮件重定向到另一个电子邮件地址**"，然后键入安全管理员的电子邮件地址， `securityadmin@contoso.com`例如。  <br/> 如果由模拟域发送电子邮件：选择 "**隔离邮件**"。|
|邮箱智能|默认情况下，当您创建新的反网络钓鱼策略时，将选择邮箱智能。 将此设置保留为 **"开"** 以获得最佳效果。|
|添加受信任的发件人和域|对于此示例，不要定义任何替代。|
|应用于|选择 **"收件人域"**。 在**以下任一情况**下，选择 "**选择**"。 选择 " **+ 添加**"。 选中域的名称旁边的复选框，例如， `contoso.com`在列表中，然后选择 "**添加**"。 选择“**完成**”。|

## <a name="delete-an-anti-phishing-or-atp-anti-phishing-policy"></a>删除反网络钓鱼或 ATP 反网络钓鱼策略

您可以使用安全&amp;合规性中心删除您创建的自定义策略。 您不能删除您的组织的默认策略。 我们建议使用安全&amp;合规性中心来查看或编辑任何 ATP 策略。

1. 转到[https://protection.office.com](https://protection.office.com)并使用你的工作或学校帐户登录。

2. 在左侧导航中的 "**威胁管理**" 下，选择 "**策略**"。

3. 在 "**策略**" 页上，选择 "**反网络钓鱼**" 或 " **ATP 反网络钓鱼**"。

4. 在 "**反钓鱼**或**ATP 反网络钓鱼**" 页面上，从列表中选择策略名称。

5. 在出现的页面上，选择 "**删除策略**"。 允许最长30分钟的更改传播到所有的 Office 365 数据中心。

## <a name="next-steps"></a>后续步骤

反网络钓鱼策略准备就绪后，可以查看报告，了解您的威胁防护功能是如何为您的组织工作的。 若要了解详细信息，请参阅以下资源：

- [查看适用于 Office 365 的报告 ATP](view-reports-for-atp.md)或[查看电子邮件安全报告](view-email-security-reports.md)

- [使用威胁浏览器（或实时检测）](threat-explorer.md)

继续在新功能的前面提供 ATP。 访问[Microsoft 365 路线图](https://www.microsoft.com/microsoft-365/roadmap?filters=O365)并了解要[添加到 ATP 的新功能](office-365-atp.md#new-features-in-office-365-atp)。
