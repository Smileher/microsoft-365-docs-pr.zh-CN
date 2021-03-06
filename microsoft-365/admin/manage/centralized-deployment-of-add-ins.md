---
title: 确定加载项的集中部署是否适用于你的组织
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: 确定您的 Office 365 租户和用户是否符合要求，以便您可以使用集中部署来部署 Office 外接程序。
ms.openlocfilehash: 78d87c5539daa77c2babb7ffa36967c5f27e3c10
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2020
ms.locfileid: "42362127"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>确定加载项的集中部署是否适用于你的组织

对于大多数客户来说，集中部署是为 Office 365 组织中的用户和组部署 Office 加载项值得推荐且功能最丰富的方式。 如果你是管理员，请使用本指南来确定你的租户和用户是否符合要求，以便你可以使用集中部署。
集中部署支持 Windows、Mac、iOS、Android 和 Online Office 应用。
加载项最长可能需要12个小时才能为所有用户显示客户端。
  
## <a name="requirements"></a>Requirements

集中部署加载项需要用户使用 Office 365 专业增强版（并使用其组织 ID 登录到 Office），并拥有 Exchange Online 和活动 Exchange Online 邮箱。 你的订阅目录目录必须处于或联合到 Azure Active Directory。
您可以查看以下 Office 和 Exchange 的特定要求，或使用[office 365 集中部署兼容性检查器](https://docs.microsoft.com/office365/admin/manage/centralized-deployment-of-add-ins?view=o365-worldwide#office-365-centralized-deployment-compatibility-checker)。

集中部署不支持以下内容：
  
- 针对 Office 2013 中 Word、Excel 或 PowerPoint 的加载项
    
- 本地目录服务
    
- 部署到 SharePoint 的加载项  

- 团队应用程序
   
- 组件对象模型 (COM) 或 Visual Studio Tools for Office (VSTO) 的加载项的部署
    
- 不包含 Exchange 的 Office 365 的部署，如 Office 365 商业版

### <a name="office-requirements"></a>Office 要求

- 对于 Word、Excel 和 PowerPoint 外接程序，您的用户必须使用下列项之一：
  - 在 Windows 设备上，版本1704或更高版本的 Office 365 专业增强版。
  - 在 Mac 上，版本15.34 或更高版本。
      - 在 iOS （仅限 iPad）上，版本2.9.18010804 或更高版本。
- 对于 Outlook，您的用户必须使用以下各项之一： 
  - Office 365 专业增强版的版本1701或更高版本。
  - Office Professional Plus 2019 或 Office Standard 2019 的版本1808或更高版本。
  - Office Professional Plus 2016 （MSI）或 Office Standard 2016 （MSI）的版本16.0.4494.1000 或更高版本\*
  - Office Professional Plus 2013 （MSI）或 Office Standard 2013 （MSI）的版本15.0.4937.1000 或更高版本\*
  - 版本16.0.9318.1000 或更高版本的 Office 2016 for Mac 
- 版本2.75.0 或更高版本的 Outlook mobile for iOS 
- 适用于 Android 的 Outlook mobile 版本2.2.145 或更高版本 
    
    * MSI 版本的 Outlook 在相应的 Outlook 功能区中显示管理员安装的加载项，而不是 "我的外接程序" 部分。
    

#### <a name="find-out-if-office-365-proplus-is-installed"></a>查明是否已安装 Office 365 ProPlus

若要使用 Office 365 专业增强版，用户必须拥有 Office 365 帐户，并且必须已分配有许可证。 有关详细信息，请参阅 [Office 365 ProPlus 概述](https://go.microsoft.com/fwlink/p/?linkid=846328)。

检测用户是否已安装 Office 365 专业增强版并最近使用过的最简单方法是使用 Microsoft Office 激活报告，该报告在 Microsoft 365 管理中心中提供。 此报表提供一张列表，列出最近 7 天、30 天、90 天或 180 天内已激活 Office 365 专业增强订阅版 的所有用户。 出于集中部署目的，Windows 或 Mac 的桌面激活是报表中的重要列。 可将报表导出至 Excel。 有关报表的详细信息，请参阅[管理中心内的 Office 365 报表 - Microsoft Office 激活](../activity-reports/microsoft-office-activations.md)。
  
如果不想使用激活报告，可以让用户在其计算机上打开 Office 应用程序（如 Word），然后选择 "**文件** \> **帐户**"。 在" **产品信息**"下，应看到" **订阅产品**"和" **Microsoft Office 365 专业增强订阅版**"，如下图所示。

![Office 应用程序中的产品信息](../../media/4bff2bb8-0690-4d22-ac1f-b8881807fa39.png)
  
有关 Office 365 专业增强订阅版 的帮助，请参阅 [Office 365 ProPlus 疑难解答提示](https://go.microsoft.com/fwlink/p/?linkid=846339)。


### <a name="exchange-online-requirements"></a>Exchange Online 要求

Microsoft Exchange 存储组织的租户中的加载项清单。 部署外接程序的管理员和接收这些外接程序的用户必须是支持 OAuth 身份验证的 Exchange Online 版本。
  
请与组织的 Exchange 管理员联系，了解正在使用哪个配置。可使用 [Test-OAuthConnectivity](https://go.microsoft.com/fwlink/p/?linkid=846351) PowerShell cmdlet 验证每个用户的 OAuth 连接。 


### <a name="office-365-centralized-deployment-compatibility-checker"></a>Office 365 集中部署兼容性检查器

通过使用 Office 365 集中部署兼容性检查器，可验证是否已经针对 Word、Excel 和 PowerPoint 将租户上的用户设置为使用集中部署。Outlook 支持不需要兼容性检查器。在[此处](https://aka.ms/officeaddindeploymentorgcompatibilitychecker)下载兼容性检查器。
  
#### <a name="run-the-compatibility-checker"></a>运行兼容性检查器
  
1. 启动提升的 PowerShell .exe 窗口。
    
2. 运行以下命令：

```powershell
Import-Module O365CompatibilityChecker
```
    
3. 运行**CompatabilityCheck**命令：

```powershell
Invoke-CompatibilityCheck
```
   这将提示您输入*_TenantDomain_* （例如， *TailspinToysIncorporated。</span>com*）和*_TenantAdmin_* 凭据（使用您的全局管理员凭据），然后请求许可。
    
> [!NOTE]
> 检查器可能需要数分钟或数小时时间来完成检查，具体取决于租户中的用户数。 
  
工具运行完毕后，会生成逗号分隔格式的输出文件 (.csv)。 默认情况下，该文件保存到**C:\windows\system32** 。 输出文件包含以下信息：
  
- 用户名
    
- 用户 ID（用户的电子邮件地址）
    
- 集中部署准备就绪 - 如果剩余的项为 true
    
- Office plan-授权的 Office 计划
    
- Office 已激活 - 如果已激活 Office
    
- 支持的邮箱 - 如果使用已启用 OAuth 的邮箱


  
## <a name="user-and-group-assignments"></a>用户和组分配

集中部署功能当前支持 Azure Active Directory 支持的大多数组，包括 Office 365 组、通讯组列表和安全组。
  
> [!NOTE]
> 当前不支持未启用邮件的安全组。 
  
集中部署支持对租户中的单个用户、组和每个人的工作分配。 集中部署支持顶级组或没有父组的组中的用户，但不支持嵌套组或有父组的组中的用户。
   
请查看以下示例，在这里，柏隼、康霓以及销售部门组被分配了加载项。由于西海岸销售部门是嵌套组，赵强和熊飞未被分配加载项。
  
![销售部门的关系图](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

   
### <a name="find-out-if-a-group-contains-nested-groups"></a>找出一个组是否包含嵌套组

若要找出一个组是否包含嵌套组，最简单的方法是查看 Outlook 内的组联系人卡片。 如果您在电子邮件的 " **To** " 字段中输入组名称，然后在解析时选择组名称，将显示它是否包含用户或嵌套组。 在以下示例中，测试组 Outlook 联系人卡片的" **成员**"选项卡显示没有用户且只有两个子组。 
  
![Outlook 联系人卡片的 "成员" 选项卡](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)
  
可以解析某个组，查看该组是否是任何组的成员，从而进行反向查询。在以下示例中，可以在 Outlook 联系人卡片的" **成员身份**"选项卡下看到子组 1 是测试组的成员。 
  
![Outlook 联系人卡片的 "成员资格" 选项卡](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)
  
或者，可以使用 Azure Active Directory 图形 API 运行查询，查找组内的组列表。有关详细信息，请参阅 [Operations on groups | Graph API reference](https://go.microsoft.com/fwlink/p/?linkid=846342)（组操作 | 图形 API 参考）。
  
### <a name="contacting-microsoft-for-support"></a>联系 Microsoft 以获取支持

如果您或您的用户在使用 Office 应用程序（Word、Excel 等）中加载外接程序时遇到问题，则可能需要与 Microsoft 支持人员联系（[了解如何](../contact-support-for-business-products.md)）。 在支持票证中提供与 Office 365 环境相关的以下信息。
  
|**平台**|**调式信息**|
|:-----|:-----|
|Office  <br/> | Charles/Fiddler 日志  <br/>  租户 ID（ [了解如何操作](https://support.office.com/article/6891b561-a52d-4ade-9f39-b492285e2c9b.aspx)）  <br/>  CorrelationID. 查看其中一个 office 页面的来源，查找相关 ID 值并将其发送给支持人员：  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">`  <br/>  `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`  <br/> |
|丰富的客户端（Windows、Mac）  <br/> | Charles/Fiddler 日志  <br/>  客户端应用程序的内部版本号（最好是从**文件/帐户**中的屏幕截图）  <br/> |
   

