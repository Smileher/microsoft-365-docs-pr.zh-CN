---
title: 内幕风险管理案例
description: 了解 Microsoft 365 中的内部人员风险管理案例
keywords: Microsoft 365，内幕风险管理，风险管理，合规性
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 6b5132cad5725e46a49b9010868ede423321f307
ms.sourcegitcommit: 87cc278ea2ddcd536ecfaa3dfae9a5ddaa502cf9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "42179173"
---
# <a name="insider-risk-management-cases"></a>内幕风险管理案例

事例是内幕风险管理的核心，允许您深入调查并对策略中定义的风险指示器生成的问题采取措施。 在需要执行进一步操作以解决员工的符合性相关问题的情况下，将从警报中手动创建案例。 每个案例的范围限定为单个员工，并且可以将员工的多个通知添加到现有事例或新案例。 在调查事例的详细信息后，您可以通过向员工发送通知、解决案例是否为良性或升级到数据或员工调查来采取行动。

## <a name="case-dashboard"></a>事例仪表板

"内幕风险管理**案例" 仪表板**允许你查看并对事例执行操作。 仪表板上的每个报告构件都会显示过去30天的信息。

- **活动案例**：正在调查的活动案例总数。
- **过去30天的事例**：创建的案例总数，按*活动*状态和*已结束*状态排序。
- **统计信息**：活动事例的平均时间，以小时、天或月为单位列出。

事例队列列出了您的组织的所有活动和已关闭的事例，以及以下事例属性的当前状态：

- **事例名称**：事例名称，在确认警告和创建事例时定义。  
- **状态**：案例的状态为 "*活动*" 或 "*已关闭*"。
- **用户**：案例的员工。
- **时间大小写打开**：自事例打开后经过的时间。
- **策略通知总数**：事例中包含的策略匹配项的数量。 如果向事例添加新警报，此数字可能会增加。
- **上次更新**时间：自已添加事例备注或在案例状态发生更改后经过的时间。
- **上次更新者**：上次更新案例的内幕风险管理分析员或调查者的姓名。

![内幕风险管理案例仪表板](../media/insider-risk-cases-dashboard.png)

使用**搜索**控件搜索特定文本的事例名称，并使用 case 筛选器按以下属性对事例进行排序：

- 状态
- 时间大小写打开、开始日期和结束日期
- 上次更新时间、开始日期和结束日期

## <a name="investigate-a-case"></a>调查案例

若要采取正确的更正措施，更深入地调查内幕风险管理警报是至关重要的。 内幕风险管理案例是中心管理工具，可深入了解员工风险活动历史记录和警报详细信息，并可浏览风险的内容和邮件。 风险分析师和调查人员也使用案例来集中查看反馈和注释，并处理案例解决问题。 

选择案例将打开案例管理工具，并允许分析师和调查人员深入了解案例的详细信息。

### <a name="case-overview"></a>案例概述

"**案例概述**" 选项卡汇总了案例的警报活动和风险级别历史记录。 "**通知**" 小组件显示了事例的策略匹配项，包括警报状态、警报风险严重性以及检测警报的时间。 **风险级别历史记录**图表显示最近30天的用户风险级别。 折线图使分析师和调查人员能够在一段时间内快速查看总体用户风险的趋势。 **风险活动内容**小部件汇总了在添加到事例中的数据类型和包含在通知中的内容。 此小部件提供了所有数据和内容集的整体视图，在这种情况下存在风险。

**事例详细信息**窗格在所有事例管理选项卡上可用，并汇总风险分析师和调查人员的案例详细信息。 其中包括以下方面：

- **事例名称**：事例的名称，以自动生成的案例序列号为前缀，以及与第一个已确认的警报匹配的策略模板相关联的风险的名称。 
- **案例状态**：事例的当前状态，"*活动*" 或 "*已关闭*"。
- **用户风险评分**：案例的用户的当前计算的风险级别。 此分数每24小时计算一次，并使用与该用户关联的所有活动警报中的警报风险分数。
- 已**确认的警报**：针对案例确认的用户的通知列表。
- **存在风险的内容**：内容列表，按内容源和类型排序。 例如，对于 SharePoint Online 中的案例通知内容，可能会看到列出的文件夹或文件名与案例中的警报的风险活动相关联。

![内幕风险管理案例详细信息](../media/insider-risk-case-details.png)

### <a name="alerts"></a>警报

"**通知**" 选项卡汇总了案例中包含的当前警报。 可以将新警报添加到现有事例中，并将其添加到已分配的**警报**队列中。 队列中列出了以下警报属性：

- 状态
- Severity
- 检测时间

从队列中选择一个警报以显示**警报详细信息**页。

使用搜索控件搜索特定文本的警报名称，并使用警报筛选器按以下属性对事例进行排序：

- 状态
- Severity
- 检测到的时间、开始日期和结束日期

### <a name="user-activity"></a>用户活动

"**用户活动**" 选项卡是对内幕风险管理解决方案中的案例进行内部风险分析和调查的最强大工具之一。 此选项卡的结构可用于快速审阅事例，包括所有警报的历史日程表、所有警报详细信息、案例中用户的当前风险分数以及用于采取措施以在案例中包含风险的控件。

![内幕风险管理用户活动](../media/insider-risk-user-activities.png)

1. **日期和时段筛选器**：默认情况下，在事例中确认的最后六个月的警报显示在用户活动图中。 您可以使用图表窗口两端的滑块控件轻松筛选图表视图，也可以在图表筛选控件中定义特定的开始日期和结束日期。
2. **风险警报活动和详细信息**：风险活动在用户活动图中直观显示为彩色气泡。 为不同类别的风险和气泡大小创建气泡与类别的风险活动数成正比。 选择一个气泡以显示每个风险活动的详细信息。 详细信息包括：
    - 风险活动的**日期**。
    - **风险活动类别**。 例如，*电子邮件中的附件发送到**从 SharePoint Online 下载*的组织或文件之外。
    - 警报的**风险分数**。 此分数是警报风险严重级别的数值分数。
    - 与警报关联的事件数。 此外，还提供了指向与风险活动相关联的每个文件或电子邮件的链接。
3. **风险活动图例**：在用户活动图的底部，通过颜色编码的图例可帮助您快速确定每个通知的风险类别。
4. **风险活动 chronology**：列出了与事例关联的所有风险警报的完整 chronology，其中包括相应警报气泡图中提供的所有详细信息。
5. **Case 操作**：用于解决事例的选项位于 "案例操作" 工具栏上。 您可以解决案例，向员工发送电子邮件通知，或升级数据或员工调查的案例。

### <a name="content-explorer"></a>内容资源管理器

"**内容资源管理器**" 选项卡允许风险分析师和调查人员查看与风险警报关联的所有单个文件和电子邮件的副本。 例如，如果在员工将数以百计的文件从 SharePoint Online 下载到 USB 设备，并且该活动触发策略警报时创建了警报，则会捕获警报的所有下载文件，并将其从内部风险管理案例中复制到原始存储源。

内容资源管理器是一个功能强大的工具，具有基本和高级的搜索和筛选功能。 若要了解有关使用内容资源管理器的详细信息，请参阅[内幕风险管理内容浏览器](insider-risk-management-content-explorer.md)。

![内幕风险管理案例内容浏览器](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>案例备注

事例中的 "**案例说明**" 选项卡是风险分析师和调查人员在案例中共享有关其工作的注释、反馈和见解的信息。 注释是对事例的永久添加，在保存备注后不能对其进行编辑或删除。 当从警报创建事例时，将自动添加 "**确认通知" 和 "创建内部" 风险情况**对话框中输入的注释作为事例注释。

事例备注仪表板按创建注释的用户显示注释，并在保存便笺后进行的时间。 若要搜索特定关键字的 case 注释文本字段，请使用事例仪表板上的 "**搜索**" 按钮，并输入特定关键字。

向事例添加注释：

1. 在[Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 "**内幕风险管理**"，然后选择 "**事例**" 选项卡。
2. 选择一个事例，然后选择 "**事例备注**" 选项卡。
3. 选择 "**添加事例注释**"。
4. 在 "**添加事例注释**" 对话框中，键入该事例的备注。 选择 "**保存**" 将注释添加到事例中，或选择 "**取消**关闭" 而不将注释保存到事例中。

### <a name="contributors"></a>参与者

事例中的 "**参与者**" 选项卡是风险分析师和调查人员可以在案例中添加其他审阅者的地方。 默认情况下，分配有 "**内幕风险管理分析员**" 和 "**内幕风险管理" 调查员**角色的所有用户都列为 "参与者" 作为每个活动和已关闭的案例。

所有内幕风险管理案例都必须使用适当的访问控制进行管理，以保持调查的机密性和完整性。 为帮助维护对事例的访问控制，用户被分配了两种类型的访问权限之一：

- **永久访问**：当从警报创建案例时，将自动向具有**内幕风险管理分析师**和**内部人员风险管理调查员**角色的用户授予永久访问权限。 永久访问权限在案例的生存期内授予对事例的完全控制权限，并授予添加其他案例参与者的功能。
- **临时访问**：仅向具有此案例永久访问权限的参与者授予临时访问权限。 通常情况下，会向需要向事例添加笔记的用户授予此访问级别。 具有临时访问权限的参与者具有除以下各项之外的所有事例管理控制：
    - 确认或消除通知的权限
    - 编辑案例的参与者的权限
    - 在内容资源管理器中查看文件和邮件的权限

向案例添加参与者：

1. 在[Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 "**内幕风险管理**"，然后选择 "**事例**" 选项卡。
2. 选择一个事例，然后选择 "**参与者**" 选项卡。
3. 选择 "**添加参与者**"。
4. 在 "**添加参与者**" 对话框中，开始键入要添加的用户的名称，然后从 "建议用户" 列表中选择用户。 此列表是从租户订阅的 Azure Active Directory 生成的。
5. 在 "**添加参与者**" 对话框中，选择参与者的访问级别。 您可以选择 "**永久**" 或 "**临时**"。
6. 选择 "**添加**" 以将用户添加为参与者，或选择 "**取消**" 关闭对话框，而不将该用户添加为参与者。

## <a name="case-actions"></a>Case 操作

风险分析师和调查人员可以通过多种方法中的一种方法执行操作，具体取决于案例的严重性、员工风险的历史记录以及贵组织的风险准则。 在某些情况下，您可能需要将案例升级到员工或数据调查，以便与组织的其他区域进行协作，并深入了解风险活动。 内幕风险管理与其他 Microsoft 365 合规性功能紧密集成，可帮助您进行端到端的解决方案管理。

### <a name="send-a-notice"></a>发送通知

在大多数情况下，创建策略匹配警报的员工操作是意外或意外的。 通过电子邮件将提醒通知发送给员工是记录案例审阅和操作的有效方法，也是用于提醒员工公司策略或让他们参加复习培训的方法。 通知通过您为内幕风险管理基础结构[创建的通知模板](insider-risk-management-notices.md)生成。

请务必记住，向员工发送通知不***会***将案例解析为 "*已关闭*"。 在某些情况下，您可能希望在向员工发送通知以查找其他风险活动而不打开新事例时，保持事例处于打开状态。 如果要在发送通知后解析一个事例，则必须在发送通知后选择 "**解决案例**" 作为后续步骤。

向分配了案例的员工发送通知：

1. 在[Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 "**内幕风险管理**"，然后选择 "**事例**" 选项卡。
2. 选择一个事例，然后选择 "案例操作" 工具栏上的 "**发送电子邮件通知**" 按钮。
3. 在 "**发送电子邮件通知**" 对话框中，选择 "**选择通知模板**" 下拉列表控件以选择通知的通知模板。 此选择将预填充通知中的其他字段。
4. 查看 "通知" 字段并根据需要进行更新。 此处输入的值将替代模板上的值。
5. 选择 "**发送**" 将通知发送给员工，或选择 "**取消**" 关闭对话框，而不向员工发送通知。 所有发送的通知都将添加到 "**事例注释**" 仪表板上的 "事例注释" 队列中。

### <a name="escalate-for-investigation"></a>升级以进行调查

在员工风险活动需要进行其他法律审查的情况下，升级员工调查的案例。 此升级在 Microsoft 365 组织中打开一个新的高级电子数据展示事例。 高级电子数据展示提供了端到端工作流，以保留、收集、查看、分析和导出对组织内部和外部法律调查做出响应的内容。 它还允许您的法律团队管理整个法律封存通知工作流，以便与案例中所涉及的保管人进行通信。 在从内幕风险管理案例创建的高级电子数据展示事例中，将审阅者指定为管理员，可帮助您的法律团队采取适当的措施并管理内容保留。 若要了解有关高级电子数据展示事例的详细信息，请参阅[Microsoft 365 中的高级 EDsicovery 概述](overview-ediscovery-20.md)。

若要将案例升级到员工调查，请执行以下操作：

1. 在[Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 "**内幕风险管理**"，然后选择 "**事例**" 选项卡。
2. 选择一个事例，然后选择 "案例操作" 工具栏上的 "**升级以进行调查**" 按钮。
3. 在 "**升级后进行调查**" 对话框中，输入新员工调查的名称。 如果需要，请输入有关事例的注释并选择 "已**升级**"。
5. 选择 "**确认**" 以创建员工调查案例，或选择 "**取消**" 关闭对话框，而不创建新的员工调查案例。

在将内幕风险管理案例升级到新的员工调查案例之后，可以在 Microsoft 365 合规性中心的**电子数据展示** > **高级**区域中查看新案例。

### <a name="resolve-the-case"></a>解决案例

在风险分析师和调查人员完成他们的审查和调查后，可以解决案例，以对事例中当前包含的所有警报执行操作。 解决案例将添加解决分类，将案例状态更改为 "*已关闭*"，并将解决操作原因自动添加到 "**事例备注**" 仪表板上的 "事例备注" 队列中。 案例将作为以下任一项进行解析：

- **良性**：在策略匹配警报被评估为低风险、非严重或误报的情况下的分类。
- 已**确认的策略违规**：在策略匹配警报被评估为危险、严重或导致恶意意图的情况的分类。

解决案例：

1. 在[Microsoft 365 合规性中心](https://compliance.microsoft.com)中，转到 "**内幕风险管理**"，然后选择 "**事例**" 选项卡。
2. 选择一个事例，然后在 "案例操作" 工具栏上选择 "**解决案例**" 按钮。
3. 在 "**解析事例**" 对话框中，选择 "**解析为**下拉列表" 控件以选择案例的解析分类。 选项为**良性**或已**确认策略违规**。
4. 在 "**解析事例**" 对话框中，在 "**执行操作**" 文本字段中输入解析分类的原因。
5. 选择 "**解决**" 以关闭该事例或选择 "**取消**" 关闭对话框而不解析事例。
