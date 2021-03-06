---
title: 在 Office 365 高级电子数据展示中运行流程模块
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
titleSuffix: Office 365
ms.date: 9/14/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: dbc1e251-0596-443b-ac9b-f398ba955b73
description: '了解使用 office 365 高级电子数据展示为分析准备 Office 365 数据的大小写文件的指南。  '
ms.openlocfilehash: eb608eeac33e0d5d06dce9d0c35cd86f4e0bc280
ms.sourcegitcommit: e741930c41abcde61add22d4b773dbf171ed72ac
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/07/2020
ms.locfileid: "42557812"
---
# <a name="run-the-process-module-in-advanced-ediscovery-classic"></a>在高级电子数据展示中运行流程模块（经典）

在**准备** \> **过程**中，将事例文件加载到高级电子数据展示中。 
  
> [!NOTE]
> 若要使用高级电子数据展示，组织必须订阅随附高级合规性加载项的 Office 365 E3，或订阅 E5。如果没有此计划，但又要试用高级电子数据展示，可以[注册 Office 365 企业版 E5 试用版](https://go.microsoft.com/fwlink/p/?LinkID=698279)。 
  
## <a name="guidelines-preparing-data-for-advanced-ediscovery"></a>指南：为高级电子数据展示准备数据

- **Quality**：明确标识与事例相关的事例文件填充。
    
- **加载**：将文件加载到高级电子数据展示可访问的位置。
    
- **文件 ID**：高级电子数据展示中的唯一文件标识符。 如果未导入任何文件标识符，高级电子数据展示将自动生成 ID。 如果在后续进程加载中映射 ID，并映射与初始进程加载不同的路径，则高级电子数据展示将替换路径（而不是添加新的文件条目）。 该 ID 可用作导出过程中的引用。 ID 值不应为 "-1"。
    
- **MD5**：此签名用于区分文件（两个文件不被视为完全重复项，除非它们具有相同的 MD5）。 默认情况下，高级电子数据展示计算文件的 MD5。 当加载的文件是文本文件时，建议加载并映射原始 MD5 值，而不是在高级电子数据展示中对其进行计算。
    
- **文件类型和名称**：
    
  - 高级电子数据展示可以处理各种格式的文件，并将加载的本机文件提取为标准\*格式，例如。TXT、HTML 或。XML. 文本文件的处理速度比本机文件更快。 提取的文本文件存储在事例文件夹中。
    
  - 不加载无法提取的文件，如系统文件或图形图像。 这些文件可能会延迟处理。
    
  - 验证文件名是否具有明显名称和路径是否正确。
    
- **文件路径**：高级电子数据展示可以加载最长为400个字符的路径长度的文件。
    
- **文本提取**：从本机文件中提取文本时，除了常规文本之外，还会提取以下内容：隐藏文本（excel 和 .doc）、隐藏列（excel）、跟踪更改（.doc）、演讲者备注（.ppt）、嵌入对象（例如，.ppt 中的 Excel 对象）。 可以在文本编辑器中查看这些内容。
    
- **Ignore Text**：此可选功能是在运行进程之后和分析前定义的。 应谨慎使用 "忽略" 文本，因为它的使用可能会降低文件分析的性能。
    
- **多语言文本**：高级电子数据展示当前不处理标记、保管人和问题的多语言名称。
    
- **元数据**：确定是否要在事例数据库中保存要保存的元数据，以供将来参考，如日期范围、文件大小、文件类型、管理员和主题。 在已加载文件而不重新运行清单或添加重新处理开销之后，可以加载元数据。 
    
  - 如果文件最初是按路径加载，则在随后导入元数据时映射 "路径" 列。 可以按 ID 引用文件并映射不同的路径。 当文件路径发生更改时，这是一种非常有用的方案。
    
  - 如果文件最初是按文件 ID 加载，则在加载元数据时映射 ID 列。 通过路径（而不是 ID）引用文件将导致使用不同的 ID 重新加载文件。 高级电子数据展示将创建文件副本，而不是加载现有文件的元数据。
    
- **系列**：无法加载没有其父（系列头部）的家庭。 
    
- **文件大小**：加载到高级电子数据展示的文件大小没有限制。 对于分析（分析、相关性等），限制为5242880个提取文本的字符。 将忽略较大的文件（例如，在相关性中，文件不参与相关性培训过程，也不会在批量计算后收到相关性分数）。
    
- **文件数量**：对于可在单个情况下处理的文件数，没有建议的限制。 性能取决于系统的资源。 
    
## <a name="filtering-files"></a>筛选文件

用户定义的标签可与一组文件相关联，以从进程或其他任务中排除它们。 每个进程会话都与一个批次 ID 相关联。 尽管批 ID 对相关专家不可见，但可使用搜索实用程序来完成此操作，方法是为当前批处理添加筛选器，并使用用户定义的标签标记所有相应的文件。 
  
## <a name="see-also"></a>另请参阅

[高级电子数据展示（经典）](office-365-advanced-ediscovery.md)
  
[运行进程模块并加载数据](run-the-process-module-and-load-data-in-advanced-ediscovery.md)
  
[查看流程模块结果](view-process-module-results-in-advanced-ediscovery.md)

