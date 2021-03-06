---
title: 了解 Microsoft 威胁防护中的高级搜寻查询语言
description: 创建你的第一个威胁搜寻查询，并了解高级搜寻查询语言的常见运算符和其他方面
keywords: 高级搜寻、威胁搜寻、网络威胁搜寻、microsoft 威胁防护、microsoft 365、mtp、m365、搜索、查询、语言、学习、第一个查询、遥测、事件、遥测、自定义检测、架构、kusto、运算符、数据类型、powershell下载，查询示例
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 5715baaccd95d975f7d15196906a6326177bbc2e
ms.sourcegitcommit: 242f051c4cf3683f8c1a5da20ceca81bde212cfc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "42982002"
---
# <a name="learn-the-advanced-hunting-query-language"></a>了解高级搜寻查询语言

**适用于：**
- Microsoft 威胁防护

高级搜寻基于 [Kusto 查询语言](https://docs.microsoft.com/azure/kusto/query/)。 你可以使用 Kusto 语法和运算符来构建查询，该查询可以在专为高级搜寻构造的[架构](advanced-hunting-schema-tables.md)中查找信息。 若要更好地了解这些概念，请运行你的第一个查询。

## <a name="try-your-first-query"></a>尝试你的第一个查询

在 Microsoft 365 安全中心中，转到 "**搜寻**" 以运行第一个查询。 使用以下示例：

```kusto
// Finds PowerShell execution events that could involve a download
union DeviceProcessEvents, DeviceNetworkEvents
| where Timestamp > ago(7d)
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
 "DownloadFile",
 "DownloadData",
 "DownloadString",
"WebRequest",
"Shellcode",
"http",
"https")
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

这是它在高级搜寻中的显示效果。

![Microsoft 威胁防护高级搜寻查询的图像](../../media/advanced-hunting-query-example-2.png)

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>描述查询并指定要搜索的表
已将简短注释添加到查询的开头，以描述它的用途。 如果你后来决定保存查询并与组织中的其他人共享它，这将会帮助。 

```kusto
// Finds PowerShell execution events that could involve a download
```

查询本身通常以表名称开头，后跟一系列由管道 (`|`) 开头的元素。 在此示例中，我们首先创建两个表的联合， `DeviceProcessEvents`并`DeviceNetworkEvents`根据需要添加管道元素。

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```
### <a name="set-the-time-range"></a>设置时间范围
第一个管道元素是范围为前七天的时间筛选器。 尽可能缩小时间范围可以确保查询运行良好、返回易于管理的结果并且不会超时。

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>检查特定进程
时间范围紧跟在搜索代表 PowerShell 应用程序的进程文件名称后。

```
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>搜索特定的命令字符串
随后，查询将在命令行中查找通常用于使用 PowerShell 下载文件的字符串。

```kusto
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
    "DownloadFile",
    "DownloadData",
    "DownloadString",
    "WebRequest",
    "Shellcode",
    "http",
    "https")
```

### <a name="customize-result-columns-and-length"></a>自定义结果列和长度 
现在，你的查询清楚地标识了要查找的数据，你可以添加定义结果外观的元素。 `project`返回特定的列， `top`并限制结果数。 这些运算符有助于确保结果格式良好且相当大且易于处理。

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

单击“**运行查询**”以查看结果。 选择查询编辑器右上角的展开图标以重点关注您的搜索查询和结果。 

![高级搜寻查询编辑器中的展开控件的图像](../../media/advanced-hunting-expand.png)

>[!TIP]
>您可以查看图表中的查询结果，并快速调整筛选器。 有关指南，请[阅读使用查询结果](advanced-hunting-query-results.md)

## <a name="learn-common-query-operators-for-advanced-hunting"></a>了解高级搜寻的常见查询运算符

你已运行第一个查询并对其组成部分有了大致了解，现在是时候回顾并学习一些基础知识了。 高级搜寻使用的 Kusto 查询语言支持多种运算符，包括以下常见的运算符。

| 运算符 | 说明和用法 |
|--|--|
| `where` | 从表中筛选出满足谓词的行的子集。 |
| `summarize` | 生成聚合输入表内容的表。 |
| `join` | 通过匹配每个表中指定列的值，合并两个表的行以形成新表。 |
| `count` | 返回输入记录集中的记录数。 |
| `top` | 返回按指定列排序的前 N 条记录。 |
| `limit` | 最多返回指定的行数。 |
| `project` | 选择要包含、重命名或删除的列，然后插入新的计算列。 |
| `extend` | 创建计算列并将其附加到结果集。 |
| `makeset` |  返回 Expr 在组中采用的一组不同值的动态 (JSON) 数组。 |
| `find` | 查找与一组表中的谓词匹配的行。 |

若要查看这些操作符的实时示例，请在高级搜寻的**入门**部分中运行它们。

## <a name="understand-data-types-and-their-query-syntax-implications"></a>了解数据类型及其查询语法含义

高级搜寻表中的数据通常分为以下数据类型。

| 数据类型 | 说明和查询含义 |
|--|--|
| `datetime` | 通常表示事件时间戳的数据和时间信息 |
| `string` | 字符串 |
| `bool` | True 或 False |
| `int` | 32 位数值  |
| `long` | 64 位数值 |

## <a name="use-sample-queries"></a>使用示例查询

**入门**部分提供了使用常用运算符的几个简单查询。 请尝试运行这些查询，并对其进行细微修改。

![高级搜寻窗口的图像](../../media/advanced-hunting-get-started.png)

>[!NOTE]
>除了基本查询示例之外，你还可以访问特定威胁搜寻方案的[共享查询](advanced-hunting-shared-queries.md)。 浏览页面左侧或 GitHub 查询存储库中的共享查询。

## <a name="access-query-language-documentation"></a>访问查询语言文档

有关 Kusto 查询语言和受支持运算符的详细信息，请参阅 [Kusto 查询语言文档](https://docs.microsoft.com/azure/kusto/query/)。

## <a name="related-topics"></a>相关主题
- [高级搜寻概述](advanced-hunting-overview.md)
- [处理查询结果](advanced-hunting-query-results.md)
- [使用共享查询](advanced-hunting-shared-queries.md)
- [跨设备和电子邮件搜寻威胁](advanced-hunting-query-emails-devices.md)
- [了解架构](advanced-hunting-schema-tables.md)
- [应用查询最佳做法](advanced-hunting-best-practices.md)
