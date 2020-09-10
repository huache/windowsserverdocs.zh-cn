---
title: 数据报传输层安全协议
description: Windows Server 安全
ms.topic: article
ms.assetid: 57b8873a-ad9c-4f2c-93e0-a2af352c6965
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 05/16/2018
ms.openlocfilehash: 1cf6c9b504a246f9b0abe344bc596434c0319c3a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640389"
---
# <a name="datagram-transport-layer-security-protocol"></a>数据报传输层安全协议

Windows Server（半年频道）、Windows Server 2016、Windows 10

本参考主题面向 IT 专业人员，介绍了数据报传输层安全 (DTLS) 协议，该协议是 Schannel 安全支持提供程序 (SSP) 的一部分。

## <a name="BKMK_DTLS"></a>
DTLS 协议是在 Windows Server 2012 和 Windows 8 中的 Schannel SSP 中引入的，它为数据报协议提供通信隐私。 有关 Windows 版本中受支持的 DTLS 版本的信息，请参阅 [TLS/SSL 中的协议 (SCHANNEL SSP) ](/windows/win32/secauthn/protocols-in-tls-ssl--schannel-ssp-)。 此协议让客户端和服务器应用程序可采用旨在防止窃听、篡改或消息伪造的方式进行通信。 DTLS 协议基于传输层安全 (TLS) 协议并提供等效的安全保证，从而减少使用 IPsec 或设计自定义应用程序层安全协议的需求。

数据报在流媒体（如游戏或安全视频会议）中很常见。 开发人员可以开发应用程序，以在 Windows 身份验证安全支持提供程序接口)  (的上下文中使用 DTLS 协议，以确保客户端和服务器之间的通信安全。 DTLS 协议建立在用户数据报协议 (UDP) 之上。 DTLS 旨在尽可能与 TLS 类似，以最大程度地减少新的安全性发明，并最大程度地减少代码和基础结构的重复使用。

可用于配置的密码套件会在可配置 TLS 的密码套件之后进行配置。 不允许使用 RC4。 Schannel 继续使用 (CNG) 下一代加密技术。 这将利用 Windows Vista 中引入的 FIPS 140 证书。

## <a name="additional-references"></a>其他参考

[IETF RFC 4347 数据报传输层安全性](http://tools.ietf.org/html/rfc4347)