---
title: RADIUS 客户端
description: 本主题概述了 Windows Server 2016 中的网络策略服务器的 RADIUS 客户端。
manager: brianlic
ms.topic: article
ms.assetid: d3a09ac9-75f8-4f57-aab4-b0fdfe110118
ms.author: lizross
author: eross-msft
ms.openlocfilehash: c8a3fbb1845bf6faf14688019a3c27169d293151
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87953873"
---
# <a name="radius-clients"></a>RADIUS 客户端

>适用于：Windows Server（半年频道）、Windows Server 2016

网络访问服务器 \( NAS \) 是一种提供对较大网络的某些级别的访问权限的设备。 使用 RADIUS 基础结构的 NAS 还是 RADIUS 客户端，它将连接请求和记帐消息发送到 RADIUS 服务器以便进行身份验证、授权和记帐。

>[!NOTE]
>客户端计算机（如便携式计算机和其他运行客户端操作系统的计算机）不是 RADIUS 客户端。 RADIUS 客户端是网络访问服务器（如无线访问点、802.1 X 身份验证交换机、虚拟专用网络 \( VPN \) 服务器和拨号服务器），因为它们使用 radius 协议来与 radius 服务器（如网络策略服务器 NPS 服务器）进行通信 \( \) 。

若要将 NPS 部署为 RADIUS 服务器或 RADIUS 代理，必须在 NPS 中配置 RADIUS 客户端。

## <a name="radius-client-examples"></a>RADIUS 客户端示例

网络访问服务器的示例：

- 提供对组织网络或 Internet 的远程访问连接的网络访问服务器。 例如，运行 Windows Server 2016 操作系统的计算机和远程访问服务，提供传统的拨号或虚拟专用网络 (VPN) 远程访问服务连接到组织 intranet。
- 无线接入点，可使用基于无线的传输和接收技术提供对组织网络的物理层访问。
- 使用传统的 LAN 技术（如 Ethernet），提供对组织网络的物理层访问权限的交换机。
- 将连接请求转发到 RADIUS 服务器的 RADIUS 代理，该 RADIUS 服务器是在 RADIUS 代理上配置的远程 RADIUS 服务器组的成员。

## <a name="radius-access-request-messages"></a>RADIUS 访问-请求消息

RADIUS 客户端创建 RADIUS 访问-请求消息并将其转发到 RADIUS 代理或 RADIUS 服务器，或者它们将访问-请求消息转发到从其他 RADIUS 客户端接收消息而不自己创建消息的 RADIUS 服务器。

RADIUS 客户端不通过执行身份验证、授权和记帐来处理访问-请求消息。 只有 RADIUS 服务器才执行这些功能。

但是，可以将 NPS 同时配置为 RADIUS 代理和 RADIUS 服务器，以便它处理某些访问-请求消息和转发其他消息。

## <a name="nps-as-a-radius-client"></a>NPS 作为 RADIUS 客户端

在将 NPS 配置为 RADIUS 代理以便将访问-请求消息转发到其他 RADIUS 服务器进行处理时，NPS 充当 RADIUS 客户端。 当将 NPS 用作 RADIUS 代理时，需要进行以下常规配置步骤：

1. 使用 NPS 代理的 IP 地址将网络访问服务器（如无线访问点和 VPN 服务器）配置为指定的 RADIUS 服务器或进行身份验证的服务器。 这将允许网络访问服务器（根据它们从访问客户端接收的信息创建访问-请求消息）将消息转发到 NPS 代理。

2. 通过添加每个网络访问服务器作为 RADIUS 客户端来配置 NPS 代理。 该配置步骤允许 NPS 代理在整个身份验证的过程中从网络访问服务器接收消息并与它们进行通信。 此外，在 NPS 代理上配置连接请求策略以指定哪些访问-请求消息会转发到一个或多个 RADIUS 服务器。 还可以通过远程 RADIUS 服务器组配置这些策略，可以告知 NPS 应将它从网络访问服务器接收的消息发送到哪里。

3. 配置 NPS 或其他远程 RADIUS 服务器组的 RADIUS 服务器从 NPS 代理接收消息。 通过将 NPS 代理配置为 RADIUS 客户端来完成该操作。

## <a name="radius-client-properties"></a>RADIUS 客户端属性

通过 NPS 控制台或通过使用适用于 NPS 或 Windows PowerShell 命令的 netsh 命令向 NPS 配置添加 RADIUS 客户端时，你要将 NPS 配置为从网络访问服务器或 RADIUS 代理接收 RADIUS 访问-请求消息。

在 NPS 中配置 RADIUS 客户端时，可以指定以下属性：

### <a name="client-name"></a>客户端名称

 RADIUS 客户端的友好名称，使用 NPS 管理单元或 NPS 的 netsh 命令时，该名称使 RADIUS 客户端更容易识别。

### <a name="ip-address"></a>IP 地址

RADIUS 客户端的 Internet 协议版本 4 \( IPv4 \) 地址或域名系统 \( DNS \) 名称。

### <a name="client-vendor"></a>客户端-供应商

RADIUS 客户端的供应商。 或者可以对客户端-供应商使用 RADIUS 标准值。

### <a name="shared-secret"></a>共享密钥

在 RADIUS 客户端、RADIUS 服务器和 RADIUS 代理之间用作密码的文本字符串。 当使用消息身份验证器属性时，共享机密还用作加密 RADIUS 消息的密钥。 必须在 RADIUS 客户端上和 NPS 管理单元中配置此字符串。

### <a name="message-authenticator-attribute"></a>消息身份验证器属性

RFC 2869 "RADIUS 扩展" 中介绍了整个 RADIUS 消息的消息摘要 5 \( MD5 \) 哈希。 如果存在 RADIUS 消息身份验证器属性，则对其进行验证。 如果验证失败，则丢弃 RADIUS 消息。 如果客户端设置需要消息身份验证器属性并且该属性不存在，则丢弃 RADIUS 消息。 建议使用消息身份验证器属性。

>[!NOTE]
>如果使用可扩展的身份验证协议 \( EAP 身份验证，则默认情况下将需要和启用消息身份验证器属性 \) 。

有关 NPS 的详细信息，请参阅[网络策略服务器 (nps) ](nps-top.md)。

