---
title: 商品先期备货贸易委员会（CFTC）规则1.31 （c-d）美国
description: 独立评估事务所验证了 Azure 和 Office 365 可以帮助金融公司满足 CFTC Rule 1.31 记录保留和不可变的存储要求。
keywords: Microsoft 365, 合规性, 产品/服务
localization_priority: None
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: M365-security-compliance
hideEdit: true
titleSuffix: Microsoft Compliance
ms.openlocfilehash: 448dbcf250a34d7c7d7acb2d3f3acc4c8de4d14b
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "41602639"
---
# <a name="commodity-futures-trading-commission-cftc-rule-131c-d-united-states"></a>商品先期备货贸易委员会（CFTC）规则1.31 （c-d）美国

## <a name="about-cftc-rule-13c-d"></a>关于 CFTC 规则1.3 （c-d）

[商品先期备货交易委员会](https://www.cftc.gov/)（CFTC）（一种独立美国联邦代理商）调节了商品先期备货和选项市场，以及最近的交换市场。  
  
长期 CFTC 规则1.31 定义了由 SEC Rule 17a-4 （f）建立的记录保留要求。 此外，它还指定必须维护电子记录5年，并且原始内容在前两年内保持 "可随时访问"，并且在整个过程中可由佣金或美国司法部门进行检查。保留期。  
  
在2017中， [CFTC 修订了其规则](https://www.cftc.gov/sites/default/files/idc/groups/public/@lrfederalregister/documents/file/2017-11014a.pdf)，修改并新式化其保留项法规，以采用更少的规范性标准，从而在维护记录的方式上提供了更大的灵活性。 这使得规则更具特定技术，从而使受管制实体能够选择最适合其业务的技术，同时维护确保保留过程的可靠性的安全措施。 修订后的规则消除了组织在两年中维护原始记录的要求，但保留了五年期维护期，这是由 CFTC 和 SEC 管控的公司的 harmonizes 做法。

## <a name="microsoft-and-cftc-rule-131c-d"></a>Microsoft 和 CFTC Rule 1.31 （c-d）

金融服务客户（代表世界上最受管控的行业之一）受复杂的规定的制约，如财务事务和不可修改状态中的相关通信保留。 最具说明性的是美国商品先期交易委员会（CFTC）的规则1.31，它 stipulates 为在电子存储介质上保留书籍和记录而对受管制实体的严格要求。 在指定的保留期之前，存储的记录必须是防篡改的，不能更改或删除它们。 Microsoft Azure 不可变 Blob 存储 with with Policy Lock 和 Microsoft Office 365 with 保留锁定可帮助金融机构满足 CFTC Rule 1.31 （c-d）的存储要求。

### <a name="microsoft-azure"></a>Microsoft Azure

若要评估与 CFTC Rule 1.31 （c-d）的 Azure 合规性，Microsoft 保留了一个独立的评估事务所，专门用于记录管理和信息治理、Cohasset 关联。 在生成的报告中， [CFTC 1.31 （c）–（d）合规性评估： Microsoft Azure 存储](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=19b08fd4-d276-43e8-9461-715981d0ea20&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_GRC_Assessment_Reports)，Cohasset 使用策略锁定选项验证了[Azure 不可变 blob 存储](https://docs.microsoft.com/azure/storage/blobs/storage-blob-immutable-storage)，用于保留不可擦除和不可改写（WORM）格式的基于时间的 blob，符合 CFTC 规则的基于原则的要求。 每个 Blob （记录）都受到保护，无法进行修改、覆盖或删除，除非所需的保留期已过期，并且已释放所有关联的合法保留期。 具有敏感工作负载的软件提供商和合作伙伴现在可以依赖 Azure 不可变 Blob 存储作为一站式车间解决方案，以实现记录保留。 金融机构现在可以构建自己的应用程序，利用这些功能，同时保持兼容性。

### <a name="microsoft-office-365"></a>Microsoft Office 365

若要评估符合 CFTC Rule 1.31 （c-d）的 Office 365 合规性，Microsoft 接洽了一个主要独立法律公司，专门从事法规问题、Covington & Burling、LLP。 在生成的报告中， [Microsoft Office 365 中的存档、数据保留和规则17A-4 合规性](https://go.microsoft.com/fwlink/?linkid=830440)中，Covington 验证了[Office 365 的保留锁定](https://docs.microsoft.com/office365/securitycompliance/retention-policies#locking-a-retention-policy)功能是否包括存档功能，这些功能使受管制的客户能够以一种有助于满足 CFTC 的记录保留要求的方式存储数据。

Office 365 中的存档有助于保留广泛的数据，包括电子邮件、语音邮件、共享文档、即时消息和第三方数据。 特别是，Office 365 中的存档使客户能够设置全局或精确的邮件保留策略，以便将数据存储在定义的时间段内，而不是以不可改写、不可擦除的格式存储。

## <a name="microsoft-in-scope-cloud-services"></a>Microsoft 范围内云服务

- [Azure](https://aka.ms/AzureCompliance)
- [Office 365](https://aka.ms/o365-compliance-framework)

## <a name="audits-reports-and-certificates"></a>审核、报告和证书

[Azure & CFTC Rule 1.31-SEC 17a-4 （f） & CFTC 1.31 （c-d）对 Azure 存储的合规性评估

[Office 365 & CFTC Rule 1.31 — Office 365 中的存档、数据保留和 SEC Rule 17a-4 合规性

## <a name="how-to-implement"></a>如何实现

- [金融服务法规](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5b483567-00b0-4d86-96ae-ee887dadb61c&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_Compliance_Guides)：符合云计算和 Microsoft online services 的关键美国规章原则的合规性地图。
- [风险评估和合规性指南](https://aka.ms/RiskGovernanceGuide)：针对 Microsoft 云服务风险评估和监管机构通知创建一个管理模型。
- [金融用例](https://docs.microsoft.com/azure/industry/financial/)：在案例概述、教程和其他资源的帮助下构建适合金融服务的 Azure 解决方案。

## <a name="resources"></a>资源

- [Microsoft 金融服务合规性计划](https://aka.ms/FSCP-Print)
- [Microsoft 商业云服务和金融服务](https://www.microsoft.com/trustcenter/cloudservices/financialservices)
- [Azure 中的金融服务合规性](https://azure.microsoft.com/resources/videos/azurecon-2015-financial-services-compliance-in-azure/)
- [Azure 金融服务云风险评估工具](https://aka.ms/FFIEC-CSDT)
- [Microsoft Office 365 保留策略](https://docs.microsoft.com/office365/securitycompliance/retention-policies)
- [Microsoft 金融服务博客](https://techcommunity.microsoft.com/t5/Financial-Services-Blog/bg-p/FinancialServicesBlog)
- [Microsoft 信任中心内的合规性](https://www.microsoft.com/trust-center/compliance/compliance-overview)

## <a name="download-the-offering-backgrounder"></a>下载产品/服务背景信息

需要此产品/服务的背景信息文档？ 请下载 [PDF](https://download.microsoft.com/download/9/A/9/9A9847FE-164A-4321-8112-50719D9EA877/CFTC1.31-Compliance.pdf)。
