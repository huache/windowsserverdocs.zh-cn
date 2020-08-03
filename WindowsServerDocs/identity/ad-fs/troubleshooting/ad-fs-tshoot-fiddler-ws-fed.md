---
title: AD FS 疑难解答-Fiddler-ws-federation
description: 本文档显示了 WS 联合身份验证交换与 AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/18/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: a85d486dc30a36d575927ba243d46a403c3a5185
ms.sourcegitcommit: 3632b72f63fe4e70eea6c2e97f17d54cb49566fd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520166"
---
# <a name="ad-fs-troubleshooting---fiddler---ws-federation"></a>AD FS 疑难解答-Fiddler-ws-federation

![AD FS 和 Windows Server 联合关系图](media/ad-fs-tshoot-fiddler-ws-fed/fiddler9.png)

## <a name="step-1-and-2"></a>步骤1和2

这是跟踪开始。  在此框架中，将看到以下内容：

![Fiddler 跟踪的开头](media/ad-fs-tshoot-fiddler-ws-fed/fiddler1.png)

请求：

- HTTP 获取我们的信赖方（http://sql1.contoso.com/SampApp)

响应：

- 响应是 HTTP 302 （重定向）。  响应标头中的传输数据显示重定向到的位置（https://sts.contoso.com/adfs/ls)
- 重定向 URL 包含 wa = wsignin1.0 1.0，告诉我们 RP 应用程序已生成 WS 联合身份验证登录请求，并将其发送到 AD FS 的/adfs/ls/终结点。  这称为 "重定向绑定"。

![响应标头中的传输数据](media/ad-fs-tshoot-fiddler-ws-fed/fiddler2.png)

## <a name="step-3-and-4"></a>步骤3和4

![继续 Fiddler 跟踪](media/ad-fs-tshoot-fiddler-ws-fed/fiddler3.png)

请求：

- HTTP 获取我们的 AD FS 服务器（sts .com）

响应：

- 响应会提示输入凭据。  这表示我们使用的是窗体 authnetication
- 单击响应的 Web 视图可查看凭据提示。

![Fiddler 跟踪的延续](media/ad-fs-tshoot-fiddler-ws-fed/fiddler6.png)

## <a name="step-5-and-6"></a>步骤5和6

![提示输入凭据提示屏幕的 Web 视图选项卡](media/ad-fs-tshoot-fiddler-ws-fed/fiddler4.png)

请求：

- HTTP POST，其中包含用户名和密码。
- 我们提供凭据。  通过查看请求中的原始数据，我们可以看到凭据

响应：

- 找到响应并创建并返回 MSIAuth 加密的 cookie。  这用于验证客户端生成的 SAML 断言。  这也称为 "身份验证 cookie"，仅当 AD FS 是 Idp 时才会出现这种情况。

## <a name="step-7-and-8"></a>步骤7和8

![Fiddler 跟踪的延续](media/ad-fs-tshoot-fiddler-ws-fed/fiddler5.png)

请求：

- 现在我们已经过身份验证，接下来对 AD FS 服务器进行另一个 HTTP 访问，并提供身份验证令牌

响应：

- 响应是 HTTP OK，这意味着 AD FS 根据提供的凭据对用户进行了身份验证
- 同时，我们将3个 cookie 设置回客户端
    - MSISAuthenticated 包含对客户端进行身份验证时的 base64 编码的时间戳值。
    - AD FS 无限循环检测机制使用 MSISLoopDetectionCookie 来停止对联合服务器的无限重定向循环中的客户端。 Cookie 数据是 base64 编码的时间戳。
    - MSISSignout 用于跟踪为 SSO 会话访问的 IdP 和所有 RPs。 调用 WS 联合身份验证注销时，将使用此 cookie。 可以使用 base64 解码器查看此 cookie 的内容。

## <a name="step-9-and-10"></a>步骤9和10

![Fiddler 跟踪的延续](media/ad-fs-tshoot-fiddler-ws-fed/fiddler7.png)

请求：

- HTTP POST

响应：

- 响应为找到

## <a name="step-11-and-12"></a>步骤11和12

![终止 Fiddler 跟踪](media/ad-fs-tshoot-fiddler-ws-fed/fiddler8.png)

请求：

- HTTP GET

响应：

- 响应正常

## <a name="next-steps"></a>后续步骤

- [AD FS 疑难解答](ad-fs-tshoot-overview.md)