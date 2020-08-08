---
title: 配置 NPS UDP 端口信息
description: 你可以使用本主题来配置网络策略服务器 (NPS) 用于在 Windows Server 2016 中远程身份验证拨入用户服务 (RADIUS) 身份验证和记帐流量的端口。
manager: brianlic
ms.topic: article
ms.assetid: 70569958-d7a7-474e-a817-6b7b5134784a
ms.author: lizross
author: eross-msft
ms.openlocfilehash: c522206fe701d47f8f0c07e7c7a64d7e6fc7074c
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87944507"
---
# <a name="configure-nps-udp-port-information"></a>配置 NPS UDP 端口信息

>适用于：Windows Server（半年频道）、Windows Server 2016

你可以使用以下过程来配置网络策略服务器 (NPS) 用于远程身份验证拨入用户服务 \( RADIUS \) 身份验证和记帐通信的端口。

默认情况下，NPS 侦听端口1812、1813、1645和1646上用于 \( \) 所有已安装网络适配器的 Internet 协议版本 6 IPv6 和 IPV4 的 RADIUS 流量。

>[!NOTE]
>如果卸载网络适配器上的 IPv4 或 IPv6，则 NPS 不会监视已卸载协议的 RADIUS 流量。

用于身份验证的1812端口值和用于记帐的1813是由 Internet 工程任务强制 \( IETF \) 在 rfc 2865 和2866中定义的 RADIUS 标准端口。 但是，默认情况下，许多访问服务器使用端口1645进行身份验证请求，使用1646进行记帐请求。 无论决定使用哪个端口号，都要确保将 NPS 和访问服务器配置为相同的端口号。

>无关紧要如果不使用 RADIUS 默认端口号，则必须在防火墙上为本地计算机配置例外，以允许新端口上的 RADIUS 流量。 有关详细信息，请参阅为[RADIUS 流量配置防火墙](nps-firewalls-configure.md)。

若要完成该过程，必须至少具有 **Domain Admins** 的成员资格或同等权限。

## <a name="to-configure-nps-udp-port-information"></a>配置 NPS UDP 端口信息

1. 打开 NPS 控制台。
2. 右键单击 "**网络策略服务器**"，然后单击 "**属性**"。
3. 单击 "**端口**" 选项卡，然后检查端口的设置。 如果 RADIUS 身份验证和 RADIUS 记帐 UDP 端口不同于提供的默认值 (1812，1645用于身份验证，1813和1646用于记帐) ，请在 "**身份验证**和**记帐**" 中键入端口设置。
4. 若要为身份验证或记帐请求使用多个端口设置，请用逗号分隔端口号。

有关管理 NPS 的详细信息，请参阅[管理网络策略服务器](nps-manage-top.md)。

有关 NPS 的详细信息，请参阅[网络策略服务器 (nps) ](nps-top.md)。
