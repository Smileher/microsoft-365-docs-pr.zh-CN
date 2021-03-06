---
title: 针对 Microsoft 365 的标识和设备访问测试环境
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 04/23/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: 创建一个 Microsoft 365 环境来测试标识和设备访问情况。
ms.openlocfilehash: e43483afc9e17de9582b2998867b53cfff7d8492
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "41600999"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>针对 Microsoft 365 的标识和设备访问测试环境

*此测试实验室指南仅可用于 Microsoft 365 企业版测试环境。*

[标识和设备访问配置](microsoft-365-policies-configurations.md)是一组功能和条件访问策略，用于保护对与 Azure Active Directory (Azure AD) 集成的所有服务的访问，包括 Microsoft 365 企业版中的 Office 365 和 Microsoft Intune。

要创建一个部署有这些策略的测试环境：

1. 根据所选的标识模型和身份验证方法，使用必备标识和安全功能来配置测试环境：

  - [仅限云](cloud-only-prereqs-m365-test-environment.md)
  - [密码哈希同步 (PHS)](phs-prereqs-m365-test-environment.md)
  - [直通身份验证 (PTA)](pta-prereqs-m365-test-environment.md)

2. 使用[常见标识和设备访问策略](identity-access-policies.md)来配置基于先决条件构建的策略并对标识和设备的保护进行测试。

## <a name="see-also"></a>另请参阅

[其他标识测试实验室指南](m365-enterprise-test-lab-guides.md#identity)

[阶段 2：标识](identity-infrastructure.md)

[Microsoft 365 企业版测试实验室指南](m365-enterprise-test-lab-guides.md)

[Microsoft 365 企业版部署](deploy-microsoft-365-enterprise.md)

[Microsoft 365 企业版文档](https://docs.microsoft.com/microsoft-365-enterprise/)
