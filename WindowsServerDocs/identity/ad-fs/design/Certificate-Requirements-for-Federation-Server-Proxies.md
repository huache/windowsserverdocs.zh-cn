---
ms.assetid: dc24adb7-385d-4a92-ab81-78ba73df0118
title: 联合服务器代理的证书要求
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 51eb0e72f52fafdb2f1b8bbb3f9a2850602c3f75
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954333"
---
# <a name="certificate-requirements-for-federation-server-proxies"></a>联合服务器代理的证书要求

在 Active Directory 联合身份验证服务 AD FS 中在联合服务器代理角色中运行的 \( 服务器 \) 需要使用安全套接字层 \( SSL \) 服务器身份验证证书。 联合服务器代理使用 SSL 服务器身份验证证书保护与 Web 客户端的 Web 服务器流量通信。

联合服务器代理通常向 Internet 上未包括在企业公钥基础结构 PKI 中的计算机公开 \( \) 。 因此，请使用由公有 \( 第三方证书颁发机构 CA 颁发的服务器身份验证证书 \- \) \( \) ，例如 VeriSign。

如果你具有联合服务器代理场，则所有联合服务器代理计算机都必须使用相同的服务器身份验证证书。 有关详细信息，请参阅 [When to Create a Federation Server Proxy Farm](When-to-Create-a-Federation-Server-Proxy-Farm.md)。

务必验证服务器身份验证证书中的使用者名称是否与 "AD FS 管理" 管理单元中指定的 "联合身份验证服务名称" 值匹配 \- 。 若要查找此值，请打开管理单元 \- ，右键 \- 单击 "**服务**"，单击 "**编辑联合身份验证服务属性**"，然后在 "**联合身份验证服务名称**" 文本框中找到该值。

有关使用 SSL 证书的一般信息，请参阅在 IIS 7.0 中配置安全套接字层 \( [http： \/ \/ go.microsoft.com \/ fwlink \/ ？LinkID \= 108544](https://go.microsoft.com/fwlink/?LinkID=108544) \) 和配置 IIS 7.0 中的服务器证书 \( [http： \/ \/ go.microsoft.com \/ fwlink \/ ？LinkID \= 108545](https://go.microsoft.com/fwlink/?LinkID=108545) \) 。

> [!NOTE]
> AD FS 联合服务器代理不需要客户端身份验证证书。

如果你使用的任何证书具有证书吊销列表 \( crl \) ，则具有配置的证书的服务器必须能够联系分发 crl 的服务器。 CRL 的类型确定了使用的端口。

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
