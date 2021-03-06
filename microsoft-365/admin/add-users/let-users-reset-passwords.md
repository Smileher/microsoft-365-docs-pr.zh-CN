---
title: 允许用户在 Office 365 中重置其密码
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5bc3f460-13cc-48c0-abd6-b80bae72d04a
description: 了解如何使用自助密码重置工具来重置密码。
ms.openlocfilehash: 87accc393d08b922ebc3f75ef1aa5ddb2d0b2955
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/24/2020
ms.locfileid: "42238152"
---
# <a name="let-users-reset-their-own-passwords"></a>允许用户重置自己的密码

因不断为用户重置密码而感到崩溃？ 作为 Microsoft 365 管理员，你可以让用户使用[自助密码重置工具](https://go.microsoft.com/fwlink/p/?LinkId=522677)，这样你就不必重置它们的密码。 减少工作量！ 
  
以下是需要了解的一些事项：
  
- 可以通过任意 Office 365 商业版、教育版或非营利组织付费的计划 **免费** 为云用户获取自助密码重置服务。但不适用于 Office 365 试用版。 
    
- 该功能使用 Azure。将在执行下面的步骤时，自动在 Azure 中 **免费** 获得此功能。如果不使用其他 Azure 功能，则不需要支付任何费用即可启用自助密码重置功能。 
    
- **如果使用的是本地 Active Directory**，则不适用以上两个点。 相反，您可以对此进行设置，但**需要付费的 AZURE AD Premium 订阅**。 

观看有关允许用户重置其自己的密码的简短视频。 <br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3AY8S] 

如果你发现此视频有帮助，请查看[适用于小型企业和 Microsoft 365 新用户的完整培训系列](https://support.office.com/article/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816)。

## <a name="let-people-reset-their-own-passwords"></a>允许用户重置自己的密码 

以下步骤将为企业中的所有人启用自助密码重置。
  
::: moniker range="o365-worldwide"
1.  在 "管理中心" 中，转到 "**设置** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">安全 & 隐私</a>" 页。

::: moniker-end

::: moniker range="o365-germany"

1. 在 "<a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">管理中心</a>" 中，转到 "**设置** \> **安全&amp;隐私**" 页。

::: moniker-end

::: moniker range="o365-21vianet"

1. 在 "<a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">管理中心</a>" 中，转到 "**设置** \> **安全&amp;隐私**" 页。

::: moniker-end

   
2. 在 "**允许你的用户重置其密码**" 下，选择 " **Azure AD 管理中心**" 的链接。 将免费获得 Azure！
  
3. 在左侧导航栏中选择 "**用户**"，然后选择 "**密码重置**"。
  
4. 在 "属性" 页上，选择 "**全部**" 以为企业中的所有人启用它，然后选择 "**保存**"。
  
5. 当你的用户登录到 Office 365 时，系统将提示他们输入其他联系信息，这可帮助他们在将来重置密码。

## <a name="related-articles"></a>相关文章

[为组织设置密码过期策略](../manage/set-password-expiration-policy.md)
  
[将个人用户密码设置为永不过期](set-password-to-never-expire.md)

[Microsoft 365 商业版培训视频](https://support.office.com/article/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816)
