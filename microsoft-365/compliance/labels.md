---
title: 保留标签概述
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: 使用保留标签可对整个组织中的数据进行分类来管理数据，并根据此分类强制执行保留规则。另外，还可以使用保留标签来在 Microsoft 365 中实施记录管理解决方案。
ms.openlocfilehash: 3bcaee41ab178ae79b1f2ef46871dadb107f3f5b
ms.sourcegitcommit: 3b2fdf159d7dd962493a3838e3cf0cf429ee2bf2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "42929446"
---
# <a name="overview-of-retention-labels"></a>保留标签概述

整个组织中可能有不同类型的内容。为了遵守行业法规和内部策略，必须采取不同的操作。例如，可能有：
  
- 至少必须**保留**一段时间的纳税申报表格。 
    
- 达到一定年限后必须**永久删除**的新闻材料。 
    
- 必须先**保留**再**永久删除**的竞争性研究。 
    
- 必须**标记为记录**以免被编辑或删除的工作签证。 
    
无论是上述哪种用途，Office 365 中的保留标签都可有助于对正确的内容执行适当的操作。借助保留标签，可对整个组织中的数据进行分类来管理数据，并根据此分类强制执行保留规则。
  
借助保留标签，你可以：
  
- **方便组织内人员手动将保留标签应用于** Outlook 网页版、Outlook 2010 及更高版本、OneDrive、SharePoint 和 Office 365 组中的内容。用户通常最了解自己处理的内容类型，因此可对数据进行分类，并应用适当策略。 
    
- **将保留标签自动应用于**符合特定条件的内容，如内容包含： 
    
    - 特定类型敏感信息。
    
    - 与所创建的查询匹配的特定关键字。
    
    - 可训练分类器的模式匹配。
    
  能否将保留标签自动应用于内容非常重要，这是因为：
    
     - 无需为用户提供有关所有分类的培训。
    
     - 无需依赖用户，即可对全部内容进行正确分类。
    
   - 用户不再需要了解数据管理策略，反而可以专注于自己的工作。

- **在 Office 365 中实现记录管理**，包括电子邮件和文档。可使用保留标签将内容分类为记录。如果这样做，既无法更改或删除保留标签，也无法编辑或删除内容。 

- **将默认保留标签应用于 SharePoint 中的文档库、文件夹或文档集**，以让到达该位置的所有文档都继承默认保留标签。  
    
在 Microsoft 365 合规中心、Microsoft 365 安全中心或 Office 365 安全与合规中心，创建保留标签。

## <a name="how-retention-labels-work-with-retention-label-policies"></a>如何结合使用保留标签和保留标签策略

使组织中的人员可使用保留标签，便于其按两步操作进行内容分类：首先创建保留标签，然后将其发布到所选位置。 发布保留标签时，将创建保留标签策略。
  
![标签角色和任务的关系图](../media/4082bc7d-c04c-4b9a-8a26-7f12565d3311.png)
  
保留标签是独立且可重复使用的构建基块，其包含在一个或多个保留标签策略中。 保留标签策略的主要目的是对一组保留标签进行分组，并指定要显示标签的位置。
  
![标签、标签策略和位置的关系图](../media/eee42516-adf0-4664-b5ab-76727a9a3511.png)
  
1. 发布保留标签时，它们将包含在保留标签策略中。 请注意，保留标签名称是不可变的，创建后将无法编辑。


2. 一个保留标签可以包含在多个保留标签策略中。

3. 一个位置也可以包括在许多保留标签策略中。    
    
3. 保留标签策略指定保留标签发布位置。
    
## <a name="only-one-retention-label-at-a-time"></a>一次只能分配一个保留标签

请务必了解，电子邮件或文档等内容一次只能分配有一个保留标签：
  
- 对于最终用户手动分配的保留标签，用户可删除或更改所分配的保留标签。
    
- 可将内容分配有的自动应用标签替换为，最终用户手动分配的保留标签。
    
- 如果最终用户已手动向内容分配保留标签，无法使用自动应用标签来替换手动分配的保留标签。
    
- 若有多个规则要分配自动应用标签，且内容满足多个规则的条件，那么分配的是年限最长规则的保留标签。
    
手动分配标签是显式分配标签；自动应用标签是隐式分配标签；显式保留标签优先于隐式标签。有关详细信息，请参阅下面的[保留原则或优先级](#the-principles-of-retention-or-what-takes-precedence)部分。

此部分中的所有信息仅适用于保留标签。请注意，除了一个保留标签之外，内容项还可以再应用有一个敏感度标签。
  
## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>保留标签需要多长时间才能生效

保留标签在发布或自动应用后不会立即生效：
  
1. 首先，需要将标签策略从管理中心同步到策略中的位置。
    
2. 然后，该位置可能需要一段时间才能使已发布的保留标签对最终用户可用，或需要一段时间将标签自动应用到内容。 所需时间长短取决于保留标签的位置和类型。
    
### <a name="published-retention-labels"></a>已发布的保留标签

如果将保留标签发布到 SharePoint 或 OneDrive，可能需要等待 1 天时间，这些保留标签才会向最终用户显示。此外，如果向 Exchange 发布保留标签，可能需要等待 7 天，这些保留标签才会向最终用户显示，并且邮箱至少必须包含 10MB 数据。
  
![手动标签生效时间关系图](../media/b19f3a10-f625-45bf-9a53-dd14df02ae7c.png)
  
### <a name="auto-apply-retention-labels"></a>自动应用保留标签

如果将保留标签自动应用于符合特定条件的内容，可能需要等待 7 天，才能将保留标签应用于与条件匹配的所有现有内容。
  
![自动应用标签生效时间关系图](../media/b8c00657-477a-4ade-b914-e643ef97a10d.png)
  
### <a name="how-to-check-on-the-status-of-retention-labels-published-to-exchange"></a>如何检查发布到 Exchange 的保留标签的状态

在 Exchange Online 中，有一个流程每 7 天运行一次，用于向最终用户提供保留标签。使用 PowerShell，可查看此流程的上次运行时间，从而确定它何时再次运行。
  
1. [连接到 Exchange Online PowerShell](https://go.microsoft.com/fwlink/?linkid=799773)。
    
2. 运行下面这些命令。
    
   ```powershell
   $logProps = Export-MailboxDiagnosticLogs <user> -ExtendedProperties
   ```

   ```powershell
   $xmlprops = [xml]($logProps.MailboxLog)
   ```

   ```powershell
   $xmlprops.Properties.MailboxTable.Property | ? {$_.Name -like "ELC*"}
   ```

在结果中，`ELCLastSuccessTimeStamp` (UTC) 属性显示系统上次处理你邮箱的时间。 如果自创建策略起未处理，则不会显示标签。 若要强制处理，请运行 `Start-ManagedFolderAssistant -Identity <user>`。
    
如果标签没有显示在 Outlook 网页版中，但你认为标签应显示，请务必清除浏览器中的缓存 (Ctrl+F5)。
    
## <a name="retention-label-policies-and-locations"></a>保留标签策略和位置

不同类型的保留标签可发布到不同位置，具体视保留标签用途而定。
  
|**如果保留标签…**|**可将标签策略应用于…**|
|:-----|:-----|
|发布给最终用户  <br/> |Exchange、SharePoint、OneDrive 和 Office 365 组  <br/> |
|根据敏感信息类型自动应用  <br/> |Exchange（仅全部邮箱）、SharePoint 和 OneDrive  <br/> |
|根据查询自动应用  <br/> |Exchange、SharePoint、OneDrive 和 Office 365 组  <br/> |
   
在 Exchange 中，自动应用（同时针对查询和敏感信息类型）的保留标签只会应用于新发送的邮件（传输中的数据），而非当前邮箱中的所有项目（静态数据）。 此外，用于敏感信息类型的自动应用的保留标签只能应用于全部邮箱；不能选择特定邮箱。
  
Exchange 公用文件夹和 Skype 不支持标签。
  
## <a name="how-retention-labels-enforce-retention"></a>保留标签如何强制执行保留

保留标签能够执行保留策略可执行的相同保留操作。 可使用保留标签执行复杂的内容计划（或文件计划）。 有关保留操作工作原理的详细信息，请参阅[保留策略概述](retention-policies.md)。
  
此外，保留标签有两个保留选项，这两个选项只能用于保留标签，而不能用于保留策略。借助保留标签，你可以：
  
- 在保留期到期时触发处置评审。这样一来，必须先评审 SharePoint 和 OneDrive 文档，然后才能删除它们。有关详细信息，请参阅[处置评审概述](disposition-reviews.md)。
    
- 保留期从内容分配有标签时开始计算，而不是根据内容年限或上次修改时间计算。 此选项仅适用于 SharePoint 网站和 OneDrive 帐户中的内容。 对于 Exchange 电子邮件，保留期限始终基于发送或接收邮件的日期，无论此处选择哪个选项，都是如此。
    
![包含标签专用选项的保留设置](../media/c49118c9-6279-4661-94db-deffa76e27ac.png)
  
## <a name="where-published-retention-labels-can-appear-to-end-users"></a>在哪些位置上发布的保留标签可向最终用户显示

如果保留标签将由最终用户分配给内容，可将保留标签发布到：
  
- Outlook 网页版
    
- Outlook 2010 及更高版本
    
- OneDrive
    
- SharePoint
    
- Office 365 组（Outlook 网页版中的组网站和组邮箱）
    
下面各部分介绍了标签如何在不同的应用程序中向组织用户显示。
  
### <a name="outlook-on-the-web"></a>Outlook 网页版

若要在 Outlook 网页版中标记项，请右键单击项，单击“分配策略”****，再选择保留标签。 
  
![Outlook 网页版中的“分配策略”菜单](../media/146a23cf-e478-4595-b2e8-f707fc4e6ea3.png)
  
在保留标签应用后，可在项顶部查看此保留标签及其执行的操作。如果电子邮件已分类且有关联的保留期，电子邮件的到期时间便一目了然。
  
![分配给 Outlook 网页版中电子邮件的标签](../media/16f6c91b-5eab-4574-9d13-6d12be00a783.png)
  
还可将保留标签应用于文件夹，在这种情况下：
  
- 文件夹中的所有项都会自动获得相同的保留标签，已向其显式应用保留标签的项除外****。显式标记的项保留现有保留标签。有关详细信息，请参阅以下关于保留原则的部分。 
    
- 如果你更改或删除文件夹的默认保留标签，文件夹中所有项的保留标签都会随之更改或删除，具有显式保留标签的项除外****。 
    
- 如果你将具有默认保留标签的项从一个文件夹移至另一个具有不同默认保留标签的文件夹，此项会获得新的默认保留标签。
    
- 如果你将具有默认保留标签的项从一个文件夹移至另一个具有不同默认保留标签的文件夹，旧的默认保留标签会遭删除。
    
### <a name="outlook-2010-and-later"></a>Outlook 2010 及更高版本

若要在 Outlook 桌面客户端中标记项目，请选择该项目。 在功能区上的“**开始**”选项卡上，单击“**分配策略**”，然后选择保留标签。 
  
![“分配策略”按钮](../media/30684dea-dd73-4e4a-9185-8e29f403b6ca.png)
  
也可以右键单击项目，在上下文菜单中单击“**分配策略**”，然后选择保留标签。 

应用保留标签后，可查看此保留标签以及基于此项目执行的操作。 如果某电子邮件应用了具有相关保留期的保留标签，则可以一目了然地查看该电子邮件的过期时间。
  
还可将保留标签应用于文件夹。 其在 Outlook​​ 2010 及更高版本中的工作原理与在 Outlook 网页版中的相同。 请参阅上一节了解详细信息。
  
### <a name="onedrive-and-sharepoint"></a>OneDrive 和 SharePoint

若要在 OneDrive 或 SharePoint 中标记文档（包括 OneNote 文件），请选择项 \> 在右上角选择“**打开细节窗格**”![信息窗格图标](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) \>“**应用保留标签**”\> 选择保留标签。 
  
还可将保留标签应用于文件夹或文档集，并能为文档库设置默认保留标签。 有关详细信息，请参阅下面的部分。
  
![SharePoint 中项的“应用标签”列表](../media/151cc83c-da57-45b0-9cd1-fd2f28a31083.png)
  
在保留标签应用于项后，可在选择项后在细节窗格中查看保留标签。
  
![细节窗格中显示的已应用标签](../media/d06e585e-29f7-4c8c-afef-629c97268b8e.png)
  
还可创建包含“标签”**** 列或“项是记录”**** 列的库的视图，这样分配给所有项的保留标签以及哪些项是记录便一目了然。不过，请注意，无法按“项是记录”**** 列筛选视图。 
  
![库自定义视图中显示的“标签”列](../media/e3392627-c0a3-405e-bb57-55f27c34cfdd.png)
  
### <a name="office-365-groups"></a>Office 365 组

发布到 Office 365 组的保留标签同时显示在，Outlook 网页版的组网站和组邮箱中。将保留标签应用于内容的过程，与上述将保留标签应用于电子邮件和文档的过程完全相同。

保留 Office 365 组内容需要使用 Office 365 组位置。即使 Office 365 组有 Exchange 邮箱，包含整个 Exchange 位置的保留策略也不会包含 Office 365 组邮箱中的内容。

此外，不可能通过使用 Exchange 位置来包含或排除某个组邮箱。 尽管 Exchange 位置最初允许选择组邮箱，但在尝试保存保留策略时，你将收到一条错误消息，表明“RemoteGroupMailbox”不是有效的 Exchange 位置选项。
  
## <a name="applying-a-retention-label-automatically-based-on-conditions"></a>根据条件自动应用保留标签

保留标签最强大的功能之一是能够将其自动应用于符合特定条件的内容。 此情况下，组织中的人员无需应用保留标签。 Office 365 会代为操作。
  
![自动应用标签的角色和任务关系图](../media/32f2f2fd-18a8-43fd-839d-72ad7a43e069.png)
  
自动应用保留标签的功能非常强大，这是因为：
  
- 无需为用户提供有关所有分类的培训。
    
- 无需依赖用户，即可对全部内容进行正确分类。
    
- 用户不再需要了解数据管理策略，反而可以专注于自己的工作。
    
可选择将保留标签自动应用于包含以下各项的内容：
  
- [特定类型敏感信息](#auto-apply-retention-labels-to-content-with-specific-types-of-sensitive-information)
    
- [与你创建的查询匹配的特定关键字](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [可训练分类器的匹配项](#auto-apply-labels-to-content-by-using-trainable-classifiers)
    
![自动应用标签的“选择条件”页](../media/classifier-pre-trained-apply-label-match-trainable-classifier.png)

自动应用保留标签最多可能需要 7 天才会应用到与你配置的条件相匹配的所有内容。
  
> [!TIP]
> 有关使用 SharePont 中的托管属性来自动应用保留标签并实施事件驱动保留的详细方案，请参阅[使用保留标签管理 SharePoint 文档的生命周期](auto-apply-retention-labels-scenario.md)。

### <a name="auto-apply-retention-labels-to-content-with-specific-types-of-sensitive-information"></a>将保留标签自动应用于包含特定类型敏感信息的内容

为敏感信息创建自动应用保留标签时，可看到与创建数据丢失防护 (DLP) 策略时相同的策略模板列表。 预配置每个策略模板以查找特定类型的敏感信息。 例如，此处显示的模板用于查找美国 ITIN、SSN 和护照号码。 若要深入了解 DLP，请参阅[数据丢失防护策略概述](data-loss-prevention-policies.md)。
  
![包含敏感信息类型的策略模板](../media/dafd87d4-c7bb-439a-ac7b-193c018f98a5.png)
  
选择策略模板后，既可以添加或删除任意类型敏感信息，也可以更改实例计数和匹配准确度。在下面的示例中，保留标签仅在以下情况下自动应用：
  
- 内容包含的这三种类型敏感信息的实例数介于 1 和 9 个之间。可删除“最大”**** 值，这样就会变为“任意”****。
    
- 检测到的敏感信息类型的匹配准确度（或可信度）至少为 75。许多敏感信息类型都是通过多个模式进行定义，其中模式的匹配准确度越高，需要发现的证据（如关键字、日期或地址）就越多，而模式的匹配准确度越低，需要发现的证据就越少。简而言之，“最小”**** 匹配准确度越低，内容就越容易与条件匹配。 
    
要详细了解这些选项，请参阅[微调规则以增加或降低匹配的难度](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match)。
    
![用于确定敏感信息类型的选项](../media/de255881-f596-4c8d-8359-e974e3a0819a.png)
  
### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>将标签自动应用于包含关键字或可搜索属性的内容

可将标签自动应用于满足特定条件的内容。目前可用的条件支持将标签应用于包含特定字词、短语或可搜索属性值的内容。可使用搜索运算符（如 AND、OR 和 NOT）优化查询。

有关查询语法的详细信息，请参阅：

- [关键字查询语言 (KQL) 语法参考](https://docs.microsoft.com/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

基于查询的标签使用搜索索引来标识内容。有关有效可搜索属性的详细信息，请参阅：

- [内容搜索的关键字查询和搜索条件](keyword-queries-and-search-conditions.md)
- [已爬网和托管属性在 SharePoint Server 中的概述](https://docs.microsoft.com/SharePoint/technical-reference/crawled-and-managed-properties-overview)

示例查询：

- Exchange
    - subject:"Quarterly Financials"
    - recipients:garthf<!--nolink-->@contoso.com
- Sharepoint 和 OneDrive for Business
    - contenttype:contract
    - site:https<!--nolink-->://contoso.sharepoint.com/sites/teams/procurement AND contenttype:contract

![查询编辑器](../media/ac5b8e5e-7453-4ec7-905c-160df57298d3.png)


### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>使用可训练分类器向内容自动应用标签

选择可训练分类器的选项后，可选择其中一个内置分类器或选择自定义分类器。 内置分类器包含**冒犯性语言**、**简历**、**源代码**、**有针对性的骚扰**、**侮辱**和**威胁**：

![选择可训练分类器](../media/retention-label-classifers.png)

要通过此选项自动应用标签，SharePoint Online 网站和邮箱必须至少有 10 MB 的数据。

有关可训练分类器的详细信息，请参阅[可训练分类器（预览版）入门](classifier-getting-started-with.md)。

有关示例配置，请参阅[如何做好准备并使用内置分类器](classifier-using-a-ready-to-use-classifier.md#how-to-prepare-for-and-use-a-built-in-classifier)。

## <a name="applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set"></a>将默认保留标签应用于 SharePoint 库、文件夹或文档集中的所有内容

除了能让人员将保留标签应用于各个文档之外，还能将默认保留标签应用于 SharePoint 库、文件夹或文档集，这样这些位置上的所有文档都会获得默认保留标签。
  
对于文档库，此操作在文档库的“**库设置**”页上完成。 选择默认保留标签时，还可选择将其应用到库中的现有项目。 
  
例如，若有“营销材料”标记，并且确定特定文档库仅包含这种类型内容，可将“营销材料”标记设置为此库中所有文档的默认标签。
  
![库“设置”页上的“应用标签”选项](../media/0787d651-63dc-43b4-8768-716a5ecc64ec.png)
  
如果将默认保留标签应用于库、文件夹或文档集中的现有项：
  
- **除**显式应用保留标签（例如，记录）的项之外，库、文件夹或文档集中的所有项都会自动获得相同的保留标签。 显式标记的项目将保留其现有标签。 有关详细信息，请参阅下面的[保留原则或优先级](#the-principles-of-retention-or-what-takes-precedence)部分。
    
- 如果你更改或删除库、文件夹或文档集的默认保留标签，库、文件夹或文档集中所有项的保留标签都会随之更改或删除，具有显式保留标签（例如，记录）的项**除外**。
    
- 如果你将具有默认保留标签的项从一个网站集、库、文件夹或文档集移至另一个网站集、库、文件夹或文档集，此项会保留现有默认保留标签，即使新位置的默认保留标签不同也是如此。 如果该项目移动前没有标签，它将使用新位置的默认保留标签。

**记录：** 如果将默认记录标签应用于库、文件夹或文档集，则会对这些位置中的所有单个项应用记录标签。 将新项移动到包含记录标签的位置时，该项将标记为记录。 但是，如果将默认保留标签更改为未将内容声明为记录的标签，则该操作**不会**从单个项中删除记录标签；这些项会保留其记录标签。 只有网站集管理员可显式删除或更改记录项的保留标签。

有关将内容声明为记录的保留标签的详细信息，请参阅[记录概述](records.md)。
    
## <a name="applying-a-retention-label-to-email-by-using-rules"></a>使用规则将保留标签应用于电子邮件

在 Outlook 2010 或更高版本中，可创建用于应用保留标签或保留策略的规则。
  
例如，可创建一条规则，将特定保留标签应用于发送到/发送自特定通讯组的所有邮件。
  
若要创建规则，请右键单击项，依次单击“规则”****、“创建规则”****、“高级选项”**** 和“规则向导”****，再选中“应用保留策略”****。
  
![包含“应用保留策略”选项的“规则向导”](../media/eeb2407c-15b6-4224-99cf-e0a00034d8ea.png)
  
## <a name="classifying-content-without-applying-any-actions"></a>对内容分类但不执行任何操作

创建保留标签时，可以不启用保留操作或其他任何操作，如下所示。在这种情况下，可以将保留标签仅用作文本标签，而不强制执行任何操作。
  
例如，可创建不含任何操作的“稍后审阅”保留标签，再将此保留标签自动应用于包含敏感信息类型的内容或已查询内容。
  
![已禁用“保留”的“标签设置”页](../media/17ce863b-a823-426e-aaad-83718465f762.png)
  
## <a name="using-retention-labels-for-records-management"></a>使用保留标签实现记录管理
    
可以使用保留标签将内容声明为记录。 这使你可以在 Office 365 中实现单一、一致的记录管理策略。 有关详细信息，请参阅[记录概述](records.md)。
  
## <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>将保留标签用作 DLP 策略中的条件

保留标签可对内容强制执行保留操作。此外，还可以将保留标签用作数据丢失防护 (DLP) 策略中的条件。也就是说，DLP 策略可对包含特定标签的内容强制执行其他操作（如限制访问）。 
  
有关详细信息，请参阅[将标签用作 DLP 策略中的条件](data-loss-prevention-policies.md#using-a-label-as-a-condition-in-a-dlp-policy)。
  
## <a name="monitor-retention-labels"></a>监视保留标签

发布或自动应用保留标签后，需要验证保留标签是否已按预期应用于内容。若要监视保留标签，可使用：
  
- **标签活动资源管理器**。使用此资源管理器（如下所示），可快速搜索和查看过去 30 天内 SharePoint 和 OneDrive for Business 中所有内容的保留标签活动。有关详细信息，请参阅[查看文档的标签活动](view-label-activity-for-documents.md)。

- “**标签分析**”页。 在 Microsoft 365 合规中心和 Microsoft 365 安全中心中，你可以快速查看顶部标签以及它们的应用位置。 你也可以查看具有特定标签的所有内容。 有关详细信息，请参阅[使用标签分析查看标签使用情况](label-analytics.md)。
    
- **数据管理报告**。使用这些报告，可快速查看过去 90 天内 Exchange、SharePoint 和 OneDrive for Business 中所有内容的保留标签趋势和活动。有关详细信息，请参阅[查看数据管理报告](view-the-data-governance-reports.md)。
    
![标签活动资源管理器](../media/671ca0cd-1457-40b4-9917-b663360afd95.png)
  
## <a name="using-content-search-to-find-all-content-with-a-specific-retention-label-applied-to-it"></a>使用内容搜索来查找所有已应用有特定保留标签的内容

在保留标签分配到内容后（无论是用户分配还是自动应用），你都可通过内容搜索来查找所有已使用特定保留标签进行分类的内容。
  
创建内容搜索时，请选择“合规性标记”**** 条件，再输入完整或部分标签名称，并使用通配符。有关详细信息，请参阅[适用于内容搜索的关键字查询和搜索条件](keyword-queries-and-search-conditions.md)。
  
![“合规性标记”条件](../media/82d6af16-59f8-462f-babb-c894b2917018.png)
  
## <a name="the-principles-of-retention-or-what-takes-precedence"></a>保留原则或优先级

内容可能或甚至很有可能有多个应用的保留策略，每个策略的操作（保留、删除或先保留再删除）和保留期都不同。优先级是什么？最高优先级是，一个策略保留的内容一定不得被另一个策略永久删除。
  
![保留原则关系图](../media/1693d6ec-b340-4805-9da3-89aa41bc6afb.png)
  
若要了解包含保留操作的不同标签是如何应用于内容的，请注意下面这些保留原则：
  
1. **保留优先于删除。** 假设一个保留策略要删除年限超过 3 年的 Exchange 电子邮件，而另一个保留策略则要将 Exchange 电子邮件先保留 5 年再删除。任何年限达到 3 年的内容都会被删除，并隐藏起来对用户不可见，但仍保留在“可恢复项”文件夹中，直到年限达到 5 年，内容才会被永久删除。 
    
2. **最长保留期优先。** 如果内容受多个内容保留策略约束，它会一直保留到最长保留期到期。 
    
3. **显式添加的位置优先于隐式添加的位置。** 也就是说： 
    
    1. 如果具有保留设置的保留标签由用户手动分配给某项目（例如 Exchange 电子邮件或 OneDrive 文档），该保留标签优先于在站点或邮箱级别分配的策略以及由文档库分配的默认保留标签。 例如，如果显式保留标签要保留 10 年，但分配给此站点的保留策略仅要保留 5 年，则优选保留标签的保留期。 自动应用保留标签被视为隐式标签，而不是显式标签，因为它们由 Office 365 自动应用。
    
    2. 如果保留策略包含特定位置（如特定用户的邮箱或 OneDrive for Business 帐户），此策略优先于应用于所有用户邮箱或 OneDrive for Business 帐户（而不是包含具体用户邮箱）的其他保留策略。
    
4. **最短删除期优先。** 同样，如果内容受多个内容删除策略约束（无保留），它将在最短保留期到期时被删除。 
    
请注意，保留原则就像是自上而下打破平局的流：如果所有策略或标签应用的规则在一个级别上是相同的，流就会向下移至下一个级别，以确定优先应用哪个规则。
  
最后，保留策略或标签无法永久删除任何保留用于电子数据展示的内容。在此类保留释放后，内容便再次符合上文所述清理流程的条件。
  
## <a name="use-retention-labels-instead-of-these-features"></a>使用保留标签代替类似功能

可将保留标签轻松应用于整个组织，及其在 Office 365（包括 Exchange、SharePoint、OneDrive 和 Office 365 组）中的内容。建议使用保留标签在 Office 365 中的任意位置上对内容进行分类或管理记录。
  
还有其他几项先前用于在 Office 365 中进行内容分类或记录管理的功能。 其如下所示。 这些功能将继续与保留标签配合使用。 尽管存在保留标签的执行不同于先前功能的情况，但是保留标签的发展会驱动未来跨 Office 365 进行记录管理。 因此往前看来，对于数据管理，建议使用保留标签，而不是这些功能。
  
### <a name="exchange-online"></a>Exchange Online

- [保留标记和保留策略](https://go.microsoft.com/fwlink/?linkid=846125)，亦称为[邮件传递记录管理 (MRM)](https://go.microsoft.com/fwlink/?linkid=846126)（仅限删除） 
    
### <a name="sharepoint-online-and-onedrive-for-business"></a>SharePoint Online 和 OneDrive for Business

- [配置就地记录管理](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a)（保留） 
    
- [记录中心简介](https://support.office.com/article/bae6ca5a-7b19-40e0-b433-e3613a747c2c)（保留） 
    
- [信息管理策略](intro-to-info-mgmt-policies.md)（仅限删除） 
    
## <a name="permissions"></a>Permissions

负责创建保留标签的合规性团队成员必须有权访问安全&amp;合规中心。 默认情况下，租户管理员有权访问此位置，并可向合规部主管及其他人员授予对安全&amp;合规中心的访问权限，而不授予租户管理员的所有权限。为此，建议转到安全&amp;合规中心内的“**权限**”页，编辑“**合规性管理员**”角色组，再向此角色组添加成员。 
  
有关详细信息，请参阅[向用户授予对 Office 365 安全与合规中心的访问权限](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)。
  
只有在创建和应用保留标签和标签策略时，才必须拥有这些权限。强制执行策略并不需要访问内容。  
## <a name="find-the-powershell-cmdlets-for-labels"></a>查找标签适用的 PowerShell cmdlet

若要使用标签 cmdlet，你需要：
  
1. [连接到 Office 365 安全与合规中心 Powershell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)
    
2. 使用这些 Office 365 安全与合规中心 cmdlet：

  - [Get-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/get-compliancetag)

  - [New-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-compliancetag)

  - [Remove-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/remove-compliancetag)

  - [Set-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/set-compliancetag)

  - [Enable-ComplianceTagStorage](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/enable-compliancetagstorage)

  - [Get-ComplianceTagStorage](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/get-compliancetagstorage)

  - [Get-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/get-retentioncompliancepolicy)

  - [New-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-retentioncompliancepolicy)

  - [Remove-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/remove-retentioncompliancepolicy)

  - [Set-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/set-retentioncompliancepolicy)

  - [Get-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/get-retentioncompliancerule)

  - [New-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-retentioncompliancerule)

  - [Remove-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/remove-retentioncompliancerule)

  - [Set-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/set-retentioncompliancerule)
