---
title: Microsoft 威胁防护先决条件
description: 了解有关 Microsoft 威胁防护的许可、硬件和软件要求以及其他配置设置
keywords: 要求、先决条件、硬件、软件、浏览器、MTP、M365、许可证、E5、A5、EMS、purchase
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: c482e46cf51cbf11960c02663221df0c136b067c
ms.sourcegitcommit: fe4beef350ef9f39b1098755cff46fa2b8e7dc4d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2020
ms.locfileid: "42857175"
---
# <a name="microsoft-threat-protection-prerequisites"></a>Microsoft 威胁防护先决条件

**适用于：**
- Microsoft 威胁防护

了解有关设置和使用 Microsoft 威胁防护的许可、硬件和软件要求以及其他配置设置。

## <a name="licensing-requirements"></a>许可要求
若要使用 Microsoft 威胁防护，您需要一个许可证或许可证组合。

### <a name="single-license"></a>单一许可证
您可以使用以下许可证*之一*：

- Microsoft 365 E5 或 A5
- Microsoft 365 E5 Security or A5 Security

### <a name="combination-of-licenses"></a>许可证组合
您还可以将用于 E5 或 A5 订阅的许可证组合用于 Office 365、*企业移动性 + 安全性（EMS）* 和 Windows。 许可证组合必须包含以下*所有*许可证：

- Office 365 E5 或 A5
- *企业移动性 + 安全性（EMS）* E5 或 A5
- Windows E5 或 A5

有关详细信息，请[查看 Microsoft 365 企业版服务计划](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise)。

> 还没有许可证？ [试用或购买 Microsoft 365 订阅](https://docs.microsoft.com/microsoft-365/commerce/try-or-buy-microsoft-365?view=o365-worldwide)

### <a name="check-your-existing--licenses"></a>检查现有许可证
转到 Microsoft 365 管理中心（[admin.microsoft.com](https://admin.microsoft.com/)）以查看现有许可证。 在管理中心，转到“计费”**** > “许可证”****。

>[!NOTE]
> 您需要在[AZURE AD 中](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles)为**帐单管理员**或**全局读者**角色分配，以便能够查看许可证信息。 如果遇到访问问题，请联系全局管理员。

## <a name="browser-requirements"></a>浏览器要求
使用 microsoft Edge、Internet Explorer 11 或任何符合 HTML 5 的 web 浏览器访问 microsoft 365 安全中心中的 Microsoft 威胁防护。

## <a name="microsoft-threat-protection-for-us-government-community-cloud-and-us-government-community-cloud-high-gcc-high-customers"></a>Microsoft 美国政府社区云和美国政府社区云高（GCC 高）客户的 Microsoft 威胁防护
目前，Microsoft 威胁防护不适用于美国 GCC 和 GCC 高级客户。 

## <a name="related-topics"></a>相关主题
- [Microsoft 威胁防护概述](microsoft-threat-protection.md)
- [打开 Microsoft 威胁防护](mtp-enable.md)
