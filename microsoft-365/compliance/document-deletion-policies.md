---
title: 文档删除策略概述
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- SPO160
ms.assetid: 55e8d858-f278-482b-a198-2e62d6a2e6e5
description: 由于合规性、法律或其他业务要求，你的组织可能需要将文档保留一段时间。 但是，如果您的组织保留的文档比所需时间长，则会带来不必要的法律风险。 使用文档删除策略，您可以通过在特定时间段后删除网站中的文档来主动降低风险，例如，在创建文档五年后，可以在用户的 OneDrive for Business 网站中删除文档。
ms.openlocfilehash: 60bf7808daad3eaead99ef64ea24be0bcfd9be0e
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2020
ms.locfileid: "42075189"
---
# <a name="overview-of-document-deletion-policies"></a>文档删除策略概述

> [!IMPORTANT]
> 向前移动时，建议使用保留策略或在 Microsoft 365 合规性中心、Microsoft 365 安全中心或 Office 365 安全&amp;合规中心（而不是文档删除策略）中创建的标签。 文档删除策略将继续与保留策略一起工作，但如果您需要保留或删除 Office 365 中任何位置的内容，我们建议使用保留策略。 有关详细信息，请参阅[使用保留策略而不是这些功能](retention-policies.md#use-a-retention-policy-instead-of-these-features)。
  
由于合规性、法律或其他业务要求，你的组织可能需要将文档保留一段时间。 但是，如果您的组织保留的文档比所需时间长，则会带来不必要的法律风险。 使用文档删除策略，您可以通过在特定时间段后删除网站中的文档来主动降低风险，例如，在创建文档五年后，可以在用户的 OneDrive for Business 网站中删除文档。
  
文档删除策略功能强大且灵活，例如，您可以：
  
- 允许网站所有者从您集中创建和管理的策略中进行选择。您还可以在网站所有者确定策略不适用于其内容的情况下，允许其选择完全退出。
    
- 针对网站集中的所有网站（如所有 OneDrive for Business 网站）强制执行一个强制性策略，或者甚至针对使用特定网站集模板（如团队网站模板）创建的所有网站集强制执行一个策略。
    
- 提供具有默认规则的默认策略，该规则会自动应用，无需网站所有者执行任何操作。
    
- 创建一个策略，其中包括可供网站所有者选择的几个删除规则。
    
您可以使用文档删除策略中心来创建和管理文档删除策略。 或者，您可以通过[创建网站集](https://go.microsoft.com/fwlink/p/?LinkID=404342)并在 "**企业**" 选项卡上选择 "**合规性策略中心**" 来手动创建策略中心。每个租户只能有一个文档删除策略中心。 
  
![文档删除策略中心首页](../media/IP-Document-Deletion-Policy-Center-home-page.png)
  
## <a name="when-to-use-document-deletion-policies"></a>使用文件删除策略的情况

除了文件删除策略，Office 365 针对网站内容提供以下保留策略：
  
- [记录管理](https://go.microsoft.com/fwlink/p/?LinkID=404250)
    
- [针对内容类型、列表和库的信息管理策略](https://go.microsoft.com/fwlink/p/?LinkID=404239)
    
- [网站策略](https://go.microsoft.com/fwlink/p/?LinkID=404242)
    
每种类型的策略都最适合特定类型的网站或数据。例如，您的组织可能拥有使用内容类型的高度结构化网站，如合同相关的金融网站或文章相关的知识库。在这种情况下，您可以使用内容类型策略。或者，您的组织可能需要保留法律文件，此时您可以使用内容类型和记录中心来实现文件计划。
  
文档删除策略不会替换记录管理或信息管理策略，这最适用于结构化数据和内容类型。 相反，当您需要全面管理对非结构化数据（如 OneDrive for Business 网站或团队网站）的自动删除时，应使用文件删除策略。
  
![显示网站内容的保留选项的图表](../media/IP-Retention-policies-for-site-content.png)
  
如果文件删除策略所应用的网站已使用内容类型策略或针对列表或库的信息管理策略，则这些策略会在文件删除策略生效时被忽略。 这表示您应该对网站进行规划，以仅使用针对结构化内容或非结构化内容的策略，而非同时使用。 有关文件删除策略如何覆盖其他策略的详细信息，请参阅[Apply or remove a document deletion policy for a site](apply-or-remove-a-document-deletion-policy-for-a-site.md)。
  
与其他策略不同，文件删除策略仅适用于文档库，而不适用于列表。
  
## <a name="deletion-policies-and-rules"></a>删除策略和规则

文件删除策略包含一个或多个删除规则，该规则指定：
  
- 直至删除的时间段。
    
- 是根据文件创建时间还是最后修改时间计算删除日期。
    
- 是永久删除文件还是将其删除到回收站中。
    
如果一个策略包含多个规则，网站所有者可以选择最适合其内容的规则。
  
![新建删除规则页](../media/IP-New-deletion-rule.png)
  
## <a name="policies-and-assignments"></a>策略和分配

创建文档删除策略后，可以将其分配到网站集模板，例如，可以将策略分配到 OneDrive for business 模板，以便它包含每个用户的 OneDrive 网站。 将策略分配到网站集模板时，这会应用于已使用该模板创建的所有网站集，以及以后使用该模板创建的任何网站集。
  
![显示 OneDrive 选项的“选择模板”页面](../media/IP-Choose-a-template.png)
  
您还可以向特定网站集分配策略，这将覆盖已分配给该网站集模板的所有策略。例如，您可以将策略分配给团队网站模板，但之后对使用该模板创建的特定网站集应用另一组策略，以覆盖之前的策略。
  
### <a name="one-mandatory-policy-or-several-policies-to-choose-from"></a>一个强制性策略或可供选择的多个策略

分配策略时，您可以选择使其成为强制性策略，从而只有该策略可供分配，并将应用于网站集中的所有网站。网站所有者不能选择退出强制性策略，这意味着在任何情况下，网站中的文件都必须遵从该删除策略。
  
除了使单个策略成为强制性策略，您还可以向网站集分配多个策略，从而允许每个网站所有者选择要应用于其网站的策略，或者甚至可以选择完全退出。例如，您可以为一般业务文件创建一个策略，并为具有不同保留计划的财务文件创建另一个策略。网站所有者通常最了解自己的网站包含哪些内容，因此也最清楚要应用哪个文件删除策略。每个网站只能应用一个策略。
  
### <a name="one-rule-or-several-rules-to-choose-from"></a>一个规则或可供选择的多个规则

反过来，每个策略可以包含多个规则，例如，用于一般业务文档的删除策略可能有两个规则：
  
- 不需要根据法律义务或持续业务需求保留保留的文档不应保留一年以上的创建。
    
- 对于有效的现行业务使用所必需的文档（需要超过一年时间），不应保留自创建日期起超过三年的时间。
    
网站所有者可以确定其网站是否包含一般业务文件，选择该删除策略，然后从策略中选择适当的规则。 您只能从当前应用于网站的策略（而不是从任何策略）中选择规则，并且该规则将应用于网站中的所有文档库。
  
## <a name="the-relationship-of-site-collections-policies-and-rules"></a>网站集、策略和规则的关系

基本关系如下：
  
可对网站集或网站集模板分配一个或多个策略，其中每个策略可以有一个或多个规则。 但是，每个站点只能有一个处于活动状态的策略，并且网站中的库在任何时候都只能有一个活动的删除规则。
  
![显示策略之间关系的图表](../media/IP-Two-policies-four-rules.png)
  
## <a name="document-deletion-policies-are-inherited"></a>文件删除策略具有继承性

与权限、导航及其他许多网站功能一样，文件删除策略具有继承性。网站所有者可以为其网站选择一个文件删除策略，所有子网站将从父网站继承该策略。子网站所有者可通过选择其他策略和规则组合来中断继承性，此时的策略会应用于所有子网站，直到继承性再次被中断。
  
## <a name="assigning-document-deletion-policies-for-the-first-time"></a>首次分配文件删除策略

请务必了解为文档删除策略指定的时间段是指自创建或修改文档以来的时间，而不是分配该策略以来的时间。 例如，您可能创建一个文件删除策略，该策略将在文件创建两年后将其永久删除，然后将该策略分配给一个网站集模板，该模板在四五年前曾用于创建几个网站集。 在这种情况下，现有网站集可能包含多个已早于删除策略指定的年份的文档，这意味着在为第一个文件分配文档删除策略后，会立即删除大量内容时候.
  
当您首次分配策略时，将对网站中的所有文件进行计算，满足删除条件的文件将被删除。这适用于所有现有文件，而不仅仅针对分配策略后新建的文件。还要记住，时间段是针对每个文件的年龄而言，而不是自首次分配策略后的时间。
  
因此，在首次将策略分配到网站之前，您应该首先考虑现有内容的年龄，以及该策略对现有内容的影响。在分配策略之前，您还需要与网站所有者就新的策略进行沟通，以便其有时间评估可能的影响。
  
## <a name="time-lag-for-propagating-policies"></a>传播策略的时间延迟

将策略分配到网站集之后，网站所有者可使用“网站设置”**** 页上的“文件删除策略”**** 链接查看和应用适用于网站的策略。 
  
除非已将策略分配给网站集，否则不会显示 "**文档删除策略**" 链接。 此外，在将策略分配给网站后，链接不会立即显示出来，在显示 "**文档删除策略**" 链接时，可能需要从策略分配到24小时。 
  
## <a name="permissions"></a>权限

将使用文件删除策略中心的合规性团队成员需要具有对策略中心和策略将应用到的网站的访问权限。我们建议您：
  
1. 创建一个安全组，其中包含文档删除策略中心的所有用户—您很可能是合规性策略管理团队。 有关详细信息，请参阅[管理启用邮件的安全组](https://go.microsoft.com/fwlink/p/?LinkID=404345)。 
    
2. 在文件删除策略中心，将网站集所有者权限分配给安全组。 有关详细信息，请参阅[网站集管理员的权限](https://go.microsoft.com/fwlink/p/?LinkID=404346)。 
    
3. 在需要将文件删除策略分配到的每个网站集中，将网站集所有者权限分配给安全组。
    
## <a name="how-document-deletion-policies-work-with-hold-policies"></a>文件删除策略如何与保留策略结合使用

保留策略可确保将所有内容保留特定时间，而文件删除策略可确保所有内容在特定时间段后删除。
  
如果需要将文件保留固定时间段，则可以将保留策略与删除策略结合使用。例如，您可以在修改文件后将其保留三年，然后设置删除策略，以在最后修改这些文件的三年后删除。
  
请注意，删除策略无法覆盖保留策略。如果网站处于保留状态，而文件删除策略删除了一个文件，那么该文件会保留在保存保留库中，与手动删除文件的方式相同。
  
## <a name="see-also"></a>另请参阅

[应用或删除网站的文件删除策略](apply-or-remove-a-document-deletion-policy-for-a-site.md)

[创建文档删除策略](create-a-document-deletion-policy.md)


