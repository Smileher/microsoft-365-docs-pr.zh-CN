---
title: 生成搜索查询
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: 使用 Microsoft 365 中的数据调查搜索数据时，使用关键字和条件缩小搜索范围。
ms.openlocfilehash: b6769d662f843622a537a5ce93c1c5331b00fc3f
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2020
ms.locfileid: "42079013"
---
# <a name="build-search-queries"></a>生成搜索查询

在构建搜索查询时，可以使用关键字来查找特定内容和条件，以缩小搜索范围，以返回与调查最相关的项目。

![使用关键字和条件缩小搜索结果范围](../media/SearchQueryBox.png)

## <a name="keyword-searches"></a>关键字搜索

在搜索查询的 "**关键字**" 框中键入关键字查询。 您可以指定关键字、电子邮件属性（如发送和接收日期）或文档属性（如文件名或文档的上次更改日期）。 可以使用采用布尔运算符的更复杂查询，例如 **AND**、**OR**、**NOT** 和 **NEAR**。 您还可以在 SharePoint 和 OneDrive （而不是电子邮件）中搜索文档中的敏感信息（如社会保险号），或搜索在外部共享的文档。 如果将 "**关键字**" 框留空，则位于指定内容位置的所有内容都将包含在搜索结果中。
    
或者，也可以选中 "**显示关键字列表**" 复选框，然后在每行中键入关键字或关键字短语。 如果执行此操作，则每行中的关键字都将通过逻辑运算符（表示为*c:s*）连接到创建的搜索查询中的**OR**运算符的功能相似。 这意味着搜索结果中包含任何行中包含任意关键字的项。

![使用关键字列表获取查询中每个关键字的统计信息](../media/KeywordListSearch.png)

为什么使用关键字列表？ 您可以获取统计信息，以显示与关键字列表中的每个关键字匹配的项目数。 这可帮助您快速识别最有效（最少）的关键字。 您还可以在关键字列表的行中使用关键字短语（括在括号中）。 有关搜索统计信息的详细信息，请参阅[搜索统计](search-statistics.md)信息。

> [!NOTE]
> 为了帮助减少由大型关键字列表导致的问题，在关键字列表中限制为最多20行。

## <a name="conditions"></a>条件
    
您可以添加搜索条件以缩小搜索范围，并返回更精致的结果集。 每个条件向开始搜索时创建和运行的搜索查询添加一个子句。 条件以逻辑方式连接到关键字查询（在 "关键字" 框中指定），逻辑运算符（表示为 " *c:c*"）与**AND**运算符的功能相似。 这意味着项目必须同时满足关键字查询和要包括在搜索结果中的一个或多个条件。 这就是条件如何帮助缩小结果范围的原理。 有关可在搜索查询中使用的条件的列表和说明，请参阅[关键字查询和搜索条件](keyword-queries-and-search-conditions.md#search-conditions)中的 "搜索条件" 部分。
