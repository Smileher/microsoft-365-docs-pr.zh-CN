---
title: 阶段 2：身份基础结构退出条件
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: 确保你的配置符合 Microsoft 365 企业版针对基于身份的服务和基础结构的条件。
ms.openlocfilehash: 433dec5e84c88dc6422619293f435f2d7199ea2e
ms.sourcegitcommit: 08a4ee7765f3eba42f0c037c5c564c581e45df3e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "42637285"
---
# <a name="phase-2-identity-infrastructure-exit-criteria"></a>阶段 2：身份基础结构退出条件

![第 2 阶段 - 标识](../media/deploy-foundation-infrastructure/identity_icon-small.png)

确保你的标识基础结构符合以下必需条件，以及你认为可选的那些条件。

另请参阅[先决条件](https://docs.microsoft.com/microsoft-365/enterprise/identity-access-prerequisites)，获得有关标识基础结构的其他建议。

<a name="crit-identity-global-admin"></a>
## <a name="required-your-global-administrator-accounts-are-protected"></a>必需：全局管理员帐户受到保护 

你已[保护 Office 365 全局管理员帐户](https://docs.microsoft.com/office365/enterprise/protect-your-global-administrator-accounts)，以避免可能导致违反Microsoft 365订阅的攻击者的凭据泄露。

如果忽略此要求，全局管理员帐户很容易受到攻击和入侵，攻击者可以获取系统范围内的数据访问权限并加以收集、销毁或勒索。

如果需要，可在[步骤 1](identity-create-protect-global-admins.md#identity-global-admin) 中进行设置以满足此要求。

### <a name="how-to-test"></a>如何测试

使用这些步骤验证是否已保护全局管理员帐户：

1. 在 PowerShell 命令提示符处运行以下 Azure Active Directory PowerShell Graph 命令。 你应该只会看到专用全局管理员帐户列表。
   ```powershell
   Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
   ```
2. 使用步骤 1 中的每个帐户登录到 Office 365。 每个登录必须要求 Azure 多重身份验证和组织中可用的最强形式的辅助身份验证。

> [!Note]
> 有关在 Office 365 中安装 Azure Active Directory PowerShell Graph 模块和登录的说明，请参阅[连接到 Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell)。

<a name="crit-identity-pim"></a>
## <a name="optional-you-have-set-up-privileged-identity-management-to-support-on-demand-assignment-of-the-global-administrator-role"></a>可选：已经设置了 Privileged Identity Management，以支持按需分配全局管理员角色

已使用[配置 Azure AD Privileged Identity Management (PIM)](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) 中的说明，在 Azure AD 租户中启用 PIM 并将全局管理员帐户配置为符合条件的管理员。

已使用[针对 Azure AD 中混合部署和云部署的特权访问安全](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices)中的建议制定路线图，以确保特权访问能够防止网络攻击者。

如果忽略此选项，全局管理员帐户可能会受到持续在线攻击，并且如果泄露，将使得攻击者能够获取、销毁或持有敏感信息进行勒索。

如果需要，可在[步骤 1](identity-create-protect-global-admins.md#identity-pim) 中设置此选项。

<a name="crit-identity-pam"></a>
## <a name="optional-you-have-configure-privileged-access-management-in-office-365"></a>可选：在 Office 365 中配置特权访问管理

你已使用[在 Office 365 中配置特权访问管理](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration)主题中的信息来启用特权访问并在组织中创建一个或多个特权访问策略。 你已配置这些策略，且实时访问已启用，可访问敏感数据或关键配置设置。

如果需要，可在[步骤 1](identity-create-protect-global-admins.md#identity-pam) 中进行设置以满足此要求。 

<a name="crit-password-prot"></a>
## <a name="optional-azure-ad-password-protection-is-banning-the-use-of-weak-passwords"></a>可选：Azure AD 密码保护禁止使用弱密码

已启用禁用[云中](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad)以及[本地 Active Directory 域服务 (AD DS)](https://docs.microsoft.com/azure/active-directory/authentication/concept-password-ban-bad-on-premises) 的错误密码以获取全局禁用密码和自定义条款（可选）。

如果需要，请执行[步骤 2](identity-secure-your-passwords.md#identity-password-prot)，这有助于你满足此条件。

<a name="crit-identity-pw-reset"></a>
## <a name="optional-users-can-reset-their-own-passwords"></a>可选：用户可以重置自己的密码

已使用 [Azure AD 自助密码重置快速部署](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started)，为你的用户配置密码重置。

如果不符合此条件，用户将依赖用户帐户管理员来重置其密码，这会导致额外的 IT 管理开销。

如果需要，请执行[步骤 2](identity-secure-your-passwords.md#identity-pw-reset)，这有助于你满足此条件。

<a name="crit-identity-sso"></a>
## <a name="optional-users-can-sign-in-using-azure-ad-seamless-single-sign-on"></a>可选：用户可以使用 Azure AD 无缝单一登录进行登录

已为组织启用 [Azure AD Connect: 无缝单一登录](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start)，以简化用户登录到基于云的应用程序（如 Office 365）的方式。

如果忽略此选项，当用户访问使用 Azure AD 租户的其他应用程序时，系统可能会提示你的用户提供凭据。

如果需要，请执行[步骤 2](identity-secure-your-passwords.md#identity-sso)，这有助于你满足此条件。

<a name="crit-identity-custom-sign-in"></a>
## <a name="optional-the-office-365-sign-in-screen-is-personalized-for-your-organization"></a>可选：个性化组织的 Office 365 登录屏幕

你已使用[将公司品牌添加到登录和访问面板页面](https://aka.ms/aadpaddbranding)，将组织的品牌添加到 Office 365 登录页面。

如果忽略此选项，你的用户将看到通用的 Office 365 登录屏幕，可能会让他们疑惑是否登录到了组织的网站。

如果需要，请执行[步骤 2](identity-secure-your-passwords.md#identity-custom-sign-in)，这有助于你满足此条件。


<a name="crit-identity-mfa"></a>
## <a name="optional-azure-multi-factor-authentication-is-enabled-for-your-users"></a>可选：已为你的用户启用 Azure 多重身份验证

你使用 [Azure 多重身份验证计划](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted)和[条件访问策略](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-getstarted#enable-multi-factor-authentication-with-conditional-access)为你的用户帐户启用了 Azure 多重身份验证 (MFA)。

如果忽略此选项，你的用户帐户会很容易受到网络攻击者的攻击，导致凭据泄露。如果用户帐户的密码遭到破坏，帐户的所有资源和功能（如管理员角色）都可供攻击者使用。这会使得攻击者能够复制、销毁或持有内部文档和其他数据，进而进行勒索。

如果需要，可在[步骤 3](identity-secure-user-sign-ins.md#identity-mfa) 中设置此选项。

### <a name="how-to-test"></a>如何测试

1.  创建一个测试用户帐户并对其分配许可证。 
2.  通过用于真实用户帐户的其他验证方法为测试用户帐户配置 Azure 多重身份验证，如向手机发送消息。 
3.  使用测试用户帐户登录到 Office 365 门户。
4.  确保 MFA 提示你输入其他验证信息且身份验证成功。 
5.  删除该测试用户帐户。

<a name="crit-identity-ident-prot"></a>
## <a name="optional-azure-ad-identity-protection-is-enabled-to-protect-against-credential-compromise-microsoft-365-e5-only"></a>可选：启用了 Azure AD Identity Protection 以防止凭据泄露（仅限 Microsoft 365 E5）

已启用 Azure AD Identity Protection，可以：

- 解决潜在标识漏洞。
- 检测可能的凭据泄露尝试。
- 调查和处理正在进行的可疑标识活动。

如果忽略此选项，你将无法检测或自动阻止凭据泄露尝试或调查标识相关的安全事件。这可能会使你的组织很容易受到凭据泄露的攻击，进而对组织的敏感数据造成威胁。

如果需要，可在[步骤 3](identity-secure-user-sign-ins.md#identity-ident-prot) 中设置此选项。


### <a name="how-to-test"></a>如何测试

1. 创建包含初始密码的测试用户帐户。
2. 使用[让用户在 Office 365 中重置自己的密码](https://docs.microsoft.com/office365/admin/add-users/let-users-reset-passwords)中的步骤来重置测试用户帐户的密码。
3. 注销，然后使用重置密码登录到测试用户帐户。
4. 删除该测试用户帐户。

<a name="crit-identity-sync"></a>
## <a name="required-for-hybrid-identity-users-and-groups-are-synchronized-with-azure-ad"></a>混合标识所必需：用户和组与 Azure AD 已同步

如果你有现有的本地 Active Directory 域服务 (AD DS)，则已使用 Azure AD Connect 将用户帐户和组从本地 AD DS 同步到 Azure AD 租户。

通过目录同步，你的用户可以使用与登录到其计算机相同的凭据登录到 Office 365 和其他 Microsoft 云服务，并访问本地资源。

必要时请执行[第 4 步](identity-add-user-accounts.md#identity-sync)，这样做有助于满足此要求。

如果忽略此要求，将具有两组用户帐户和组：

- 位于本地 AD DS 的用户帐户和组
- 位于 Azure AD 租户组的用户帐户和组

在此状态下，两组用户帐户和组必须由 IT 管理员和用户手动维护。这会不可避免地导致帐户、密码和组不同步。

### <a name="how-to-test"></a>如何测试
要验证本地凭据身份验证是否正常运行，请使用本地凭据登录到 Office 门户。

要验证目录同步正常运行，请执行以下操作：

1.  在 AD DS 中创建新的测试组。
2.  等待同步时间。
3.  检查 Azure AD 租户以验证新测试组的名称是否出现。

<a name="crit-identity-sync-health"></a>
## <a name="optional-directory-synchronization-is-monitored"></a>可选：监控目录同步

已使用[使用 Azure AD Connect Health 进行同步](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-sync)（适用于密码同步）或[在 AD FS 中使用 Azure AD Connect Health](https://docs.microsoft.com/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs)（适用于联合身份验证），并部署了 Azure 的 AD Connect Health，其中涉及：

- 在每个本地标识服务器上安装 Azure AD Connect Health 代理。
- 使用 Azure AD Connect Health 门户监控持续同步的状态。

如果忽略此选项，则可以更准确地评估基于云的身份基础结构状态。

如果需要，可在[步骤 4](identity-add-user-accounts.md#identity-sync-health) 中设置此选项。

### <a name="how-to-test"></a>如何测试
Azure AD Connect Health 门户显示本地域控制器和持续同步的当前和正确状态。


<a name="crit-identity-pw-writeback"></a>
## <a name="optional-password-writeback-is-enabled-for-your-users"></a>可选：为你的用户启用密码写回功能

已使用 [Azure AD SSPR 密码写回](https://docs.microsoft.com/azure/active-directory/active-directory-passwords-getting-started)中的说明为 Microsoft 365 企业版订阅的 Azure AD 租户启用密码写回。

如果忽略此选项，未连接到本地网络的用户必须通过 IT 管理员重置或解除锁定其 AD DS 密码。

如果需要，可在[步骤 4](identity-add-user-accounts.md#identity-pw-writeback) 中设置此选项。

>[!Note]
>需要密码写回才可充分利用 Azure AD Identity Protection 功能，例如，当 Azure AD 检测到高风险的帐户泄露时要求用户更改其本地密码。
>

### <a name="how-to-test"></a>测试操作

通过更改 Office 365 中的密码可以使测试密码写回。 你应该能够使用你的帐户和新密码访问本地 AD DS 资源。

1. 在本地 AD DS 中创建测试用户帐户，允许进行目录同步，然后在 Microsoft 365 管理中心中授予 Microsoft 365 Enterprise 许可证。
2. 从加入到本地 AD DS 域的远程计算机，使用测试用户帐户的凭据登录到计算机和 Office 门户。
3. 选择“**设置”>“Office 365 设置”>“密码”>“更改密码**”。
4. 键入当前密码、键入新密码，然后确认。
5. 注销 Office 门户和远程计算机，然后使用测试用户帐户及其新密码登录计算机。 这可以证明你可以使用 Azure AD 租户更改本地 AD DS 用户帐户的密码。

### <a name="how-to-test"></a>如何测试

使用用户帐户名称及 Azure 多重身份验证登录到 Office 365 门户。 应在登录页面上看到自定义的品牌元素。


<a name="crit-identity-self-service-groups"></a>
## <a name="optional-self-service-group-management-is-enabled-for-specific-azure-ad-security-and-office-365-groups"></a>可选：为特定 Azure AD 安全和 Office 365 组启用了自助服务组管理

已确定哪些组适用于自助服务管理，对所有者说明了组管理工作流和职责，并为这些组[在 Azure AD 中设置自助服务管理](https://docs.microsoft.com/azure/active-directory/active-directory-accessmanagement-self-service-group-management)。

如果忽略此选项，则所有 Azure AD 组管理任务必须由 IT 管理员执行。

如果需要，可在[步骤 5](identity-use-group-management.md#identity-self-service-groups) 中设置此选项。

### <a name="how-to-test"></a>如何测试
1.  在具有 Azure 门户的 Azure AD 中创建测试用户帐户。
2.  使用测试用户帐户登录并创建测试 Azure AD 安全组。
3.  注销，然后使用 IT 管理员帐户登录。
4.  针对测试用户帐户，配置测试安全组进行自助服务管理。
5.  注销，然后使用测试用户帐户登录。
6.  使用 Azure 门户将成员添加到测试安全组。
7.  删除测试安全组和测试用户帐户。

<a name="crit-identity-dyn-groups"></a>
## <a name="optional-dynamic-group-membership-settings-automatically-add-user-accounts-to-groups-based-on-user-account-attributes"></a>可选：动态组成员身份设置根据用户帐户属性自动将用户帐户添加到组

你已确定 Azure AD 动态组集并使用 [Azure Active Directory 中基于属性的动态组成员身份](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal)中的说明来创建组和规则（用于确定用户帐户属性集和组成员身份值）。

如果忽略此选项，则随着添加新帐户或更改用户帐户属性，需要手动设置组成员身份。例如，如果某人从销售部门移动到会计部门，则必须：

- 更新该用户帐户的部门属性值。
- 从销售组中手动删除此人。
- 手动将其添加到会计组。

如果销售和会计组是动态的，只需更改该用户帐户的部门值即可。

如果需要，可在[步骤 5](identity-use-group-management.md#identity-dyn-groups) 中设置此选项。

### <a name="how-to-test"></a>如何测试

1. 在具有 Azure 门户的 Azure AD 中创建测试动态组，并对名为“test1”的部门配置规则。
2. 在 Azure AD 中创建测试用户帐户并将部门属性设为“test1”。
3. 检查用户帐户属性，以确保其已成为测试动态组的成员。
4. 将测试用户帐户的部门属性值更改为“test2”。
5. 检查用户帐户属性，以确保其不再是测试动态组的成员。
6. 删除测试动态组和测试用户帐户。

<a name="crit-identity-group-license"></a>
## <a name="optional-group-based-licensing-to-automatically-assign-and-remove-licenses-to-user-accounts-based-on-group-membership"></a>可选：基于组的许可能够根据组成员身份自动分配和删除用户帐户的许可证

为相应 Azure AD 安全组[启用基于组的许可](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-group-assignment-azure-portal)，以便自动分配或取消分配适用于 Microsoft 365 Enterprise 的许可证。

如果忽略此选项，则必须手动执行以下操作：

- 向希望访问的新用户分配许可证。
- 取消分配给不再隶属于贵公司或不再有权访问的用户许可证。

如果需要，可在[步骤 5](identity-use-group-management.md#identity-group-license) 中设置此选项。

### <a name="how-to-test"></a>如何测试

1. 在具有 Azure 门户的 Azure AD 中创建测试安全组，并配置基于组的许可来分配 Microsoft 365 Enterprise 许可证。
2. 在 Azure AD 中创建测试用户帐户并将其添加到测试安全组。
3. 在 Microsoft 365 管理中心中检查用户帐户的属性，确保其分配了 Microsoft 365 Enterprise 许可证。
4. 从测试安全组删除测试用户帐户。
5. 检查用户帐户的属性，确保它不再分配有 Microsoft 365 Enterprise 许可证。
6. 删除测试安全组和测试用户帐户。


<a name="crit-identity-access-reviews"></a>
## <a name="optional-access-reviews-configured-and-being-used-to-monitor-access"></a>可选：访问审核已配置并正用于监视访问

你已使用这些文章来配置不同类型的访问权限查看，以监视组成员身份、访问企业应用程序和角色分配：

- [组和应用](https://docs.microsoft.com/azure/active-directory/governance/create-access-review)
- [Azure AD 角色](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Azure 资源角色](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

如果需要，可在[步骤 6](identity-configure-identity-governance.md#identity-access-reviews) 中设置此选项。


## <a name="results-and-next-steps"></a>结果和后续步骤

Microsoft 365 中的标识基础结构使用强身份验证、受保护的管理员帐户以及简化的用户访问和管理。

|||
|:-------|:-----|
|![第 3 阶段：Windows 10 企业版](../media/deploy-foundation-infrastructure/win10enterprise_icon-small.png)| 如果你正在执行 Microsoft 365 企业版端到端部署的各个阶段，下一个阶段是 [Windows 10 企业版](windows10-infrastructure.md)。 |

