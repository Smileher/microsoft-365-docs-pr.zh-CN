---
title: 第 1 阶段：网络基础结构退出条件
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/23/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: 确保你的配置符合 Microsoft 365 企业版针对网络基础结构的条件。
ms.openlocfilehash: 1ace68fd19c62e4dc389604c1b0c02ddc18b52dc
ms.sourcegitcommit: 93e6bf1b541e22129f8c443051375d0ef1374150
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "42633200"
---
# <a name="phase-1-networking-infrastructure-exit-criteria"></a>第 1 阶段：网络基础结构退出条件

![第 1 阶段 - 网络](../media/deploy-foundation-infrastructure/networking_icon-small.png)

确保你的网络基础结构符合以下必需条件，以及你认为可选的那些条件。

<a name="crit-networking-step1"></a>
## <a name="required-your-network-is-ready-for-microsoft-365-enterprise"></a>必需：网络已准备就绪可供 Microsoft 365 企业版使用

- 你的办公室有足够的 Internet 带宽来处理 Microsoft 365 流量，包括 Office 365、Microsoft Intune 以及 Windows 10 企业版安装和更新。
- 你的整个网络都映射到 [Office 365 参考体系结构](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#BKMK_P2)。
- 你的网络更改已经过试用和测试，符合流量延迟要求。

如果需要，可在[步骤 1](networking-provide-bandwidth-cloud-services.md) 中进行设置以满足此要求。

<a name="crit-networking-step2"></a>
## <a name="required-your-local-offices-have-local-internet-connections-and-name-resolution"></a>必需：本地办公室具有本地 Internet 连接和名称解析

通过本地 ISP（其 DNS 服务器使用在 Internet 上标识其位置的本地公用 IP 地址）来配置每个本地办公室的 Internet 访问。这可确保访问 Microsoft 365 云服务尽可能地获得最佳性能。

如果每个分支机构不使用本地 ISP，则性能可能会受到影响，因为网络通信必须遍历组织的主干线或由远程前端服务器提供服务的数据请求。

### <a name="how-to-test"></a>如何测试
使用该办公室中设备上的工具或网站来确定代理服务器所使用的公用 IP 地址。例如，使用[我的 IP 地址是什么](https://www.whatismypublicip.com/)网页。这个由 ISP 分配的公用 IP 地址在地理位置上应为本地。它不应是来自总部的公用 IP 地址范围或来自基于云的网络安全供应商。

如果需要，可在[步骤 2](networking-dns-resolution-same-location.md) 中进行设置以满足此要求。

<a name="crit-networking-step3"></a>
## <a name="optional-unnecessary-network-hairpins-are-removed"></a>可选：删除不必要的网络回流

检查网络回流并为所有办公室确定这些回流对性能的影响。在可能的情况下删除网络回流，或与第三方网络或安全提供商协作，以实现与其网络对等的最优 Microsoft 365。

如果需要，可在[步骤 3](networking-avoid-network-hairpins.md) 中设置此选项。


<a name="crit-networking-step4"></a>
## <a name="optional-you-have-configured-traffic-bypass-on-your-internet-browsers-and-edge-devices"></a>可选：在 Internet 浏览器和边缘设备上配置流量旁路

已向本地 Internet 浏览器部署最新 PAC 文件，以使 Microsoft 365 DNS 域名的流量绕过代理服务器。

配置了网络外围设备（例如，防火墙、SSL 中断和检查以及数据包检查设备）以使用流量旁路或尽量少处理 Microsoft 365 终结点的“优化”和“允许”类别的流量。


### <a name="how-to-test"></a>如何测试

使用网络外围设备上的日志记录工具，以确保到 Microsoft 365 目标的流量不遭到检查、解密或阻止。

如果需要，可在[步骤 4](networking-configure-proxies-firewalls.md) 中设置此选项。


<a name="crit-networking-step5"></a>
## <a name="optional-your-clients-and-office-365-applications-are-configured-for-optimal-performance"></a>可选：配置客户端和 Office 365 应用程序以优化性能

已优化客户端设备上的传输控制协议 (TCP) 设置，以及 Exchange Online、Skype for Business Online、SharePoint Online 和 Project Online 服务。

如果需要，可在[步骤 5](networking-optimize-tcp-performance.md) 中设置此选项。

## <a name="results-and-next-steps"></a>结果和后续步骤

你的 Intranet 用户已准备好通过有效的网络路径或在 Internet 上使用 Microsoft 365 云服务。

|||
|:-------|:-----|
|![第 2 阶段 - 标识](../media/deploy-foundation-infrastructure/identity_icon-small.png)| 如果你正在执行 Microsoft 365 企业版端到端部署的各个阶段，下一个阶段是[标识](identity-infrastructure.md)。 |
