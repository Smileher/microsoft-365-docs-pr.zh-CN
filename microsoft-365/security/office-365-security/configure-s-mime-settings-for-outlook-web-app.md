---
title: 在 Exchange Online 中为 web 上的 Outlook 配置 S/MIME 设置
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c7dee22c-9b5b-425c-91a9-d093204ff84e
ms.collection:
- M365-security-compliance
description: Exchange online 管理员在 Exchange Online 中查看和配置 Outlook 网页中的 S/MIME 设置时需要执行的操作的简短说明。
ms.openlocfilehash: 354b247c2b0e0e610e6cb0626f4a404b582db717
ms.sourcegitcommit: c2a36b16e354e20db5fd6275175ca856eae55bfc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2020
ms.locfileid: "41960318"
---
# <a name="configure-smime-settings-in-exchange-online-for-outlook-on-the-web"></a>在 Exchange Online 中为 web 上的 Outlook 配置 S/MIME 设置

作为 Exchange Online 管理员，您可以设置 web 上的 Outlook （以前称为 "Outlook Web App"），以允许发送和接收受 S/MIME 保护的邮件。 使用**get-smimeconfig**和**Get-smimeconfig** Cmdlet 在 Exchange Online PowerShell 中查看和管理此功能。 若要连接到 Exchange Online PowerShell，请参阅[连接到 Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)。

有关语法和参数的详细信息，请参阅[get-smimeconfig](https://docs.microsoft.com/powershell/module/exchange/encryption-and-certificates/get-smimeconfig)和[get-smimeconfig](https://docs.microsoft.com/powershell/module/exchange/encryption-and-certificates/set-smimeconfig)。

## <a name="considerations-for-new-microsoft-edge-chromium-based"></a>新 Microsoft Edge 的注意事项（基于 Chromium）

若要在新的[Microsoft edge](https://www.microsoft.com/windows/microsoft-edge) web 浏览器中使用 web 上的 Outlook 中的 S/MIME，您（或另一个管理员）必须设置和配置名为**ExtensionInstallForcelist**的 microsoft Edge 浏览器策略，以在新 Microsoft Edge 中安装 microsoft S/MIME 扩展。 策略值为`maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx`。 请注意，应用此策略需要加入域的计算机，因此在新的 Microsoft Edge 浏览器中使用 S/MIME 实际上需要加入域的计算机。

有关**ExtensionInstallForcelist**策略的详细信息，请参阅[ExtensionInstallForcelist](https://docs.microsoft.com/DeployEdge/microsoft-edge-policies#extensioninstallforcelist)。

此步骤是使用新的 Microsoft Edge 的先决条件;它不会替换用户安装的 S/MIME 控件。 在首次使用 S/MIME 时，系统会提示用户在 web 上的 Outlook 中下载并安装 S/MIME 控件。 或者，用户可以在其 Outlook 的 web 设置中主动转到**S/MIME** ，以获取该控件的下载链接。

## <a name="considerations-for-chrome"></a>Chrome 注意事项

若要在 Google Chrome web 浏览器中使用 web 上的 Outlook 中的 S/MIME，您（或另一个管理员）必须设置和配置名为**ExtensionInstallForcelist**的 Chromium 策略，以在 Chrome 中安装 Microsoft S/mime 扩展。 策略值为`maafgiompdekodanheihhgilkjchcakm;https://outlook.office.com/owa/SmimeCrxUpdate.ashx`。 请注意，应用此策略需要加入域的计算机，因此使用 Chrome 中的 S/MIME 可有效地要求加入域的计算机。

有关**ExtensionInstallForcelist**策略的详细信息，请参阅[ExtensionInstallForcelist](https://cloud.google.com/docs/chrome-enterprise/policies/?policy=ExtensionInstallForcelist)。

此步骤是使用 Chrome 的先决条件;它不会替换用户安装的 S/MIME 控件。 在首次使用 S/MIME 时，系统会提示用户在 web 上的 Outlook 中下载并安装 S/MIME 控件。 或者，用户可以在其 Outlook 的 web 设置中主动转到**S/MIME** ，以获取该控件的下载链接。

## <a name="for-more-information"></a>更多信息

[邮件签名和加密的 S/MIME](s-mime-for-message-signing-and-encryption.md)
