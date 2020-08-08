---
title: AD FS 故障排除-Windows 集成身份验证
description: 本文档介绍如何排查 windows 集成身份验证问题
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 02/21/2017
ms.topic: article
ms.openlocfilehash: 4c1823e1cbfc58e50c7231293b846c31480e01a6
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954153"
---
# <a name="ad-fs-troubleshooting---integrated-windows-authentication"></a>AD FS 故障排除-Windows 集成身份验证
集成的 Windows 身份验证使用户能够使用其 Windows 凭据登录，并使用 Kerberos 或 NTLM (SSO) 上体验单一登录。

## <a name="reason-integrated-windows-authentication-fails"></a>Windows 集成身份验证失败的原因
Windows 集成身份验证失败的主要原因有三个。 它们分别是：
    - 服务主体名称 (SPN) 配置错误
    - 通道绑定令牌
    - Internet Explorer 配置

## <a name="spn-misconfiguration"></a>SPN 配置错误
服务主体名称 (SPN) 是服务实例的唯一标识符。 Kerberos 身份验证使用 Spn 将服务实例与服务登录帐户相关联。 这允许客户端应用程序请求服务对帐户进行身份验证，即使客户端没有帐户名称。

如何将 SPN 与 AD FS 一起使用的示例如下所示：
1. Web 浏览器查询 Active Directory 来确定哪个服务帐户正在运行 sts.contoso.com
2. Active Directory 通知浏览器它是 AD FS 服务帐户。
3. 浏览器将获取 AD FS 服务帐户的 Kerberos 票证。

如果 AD FS 服务帐户配置错误或 SPN 错误，则这可能会导致问题。  查看网络跟踪时，可能会出现错误，如 KRB 错误： KRB5KDC_ERR_S_PRINCIPAL_UNKNOWN。

使用网络跟踪 (例如 Wireshark) 可以确定浏览器尝试解析的 SPN，然后使用 "setspn-Q" 命令行工具， <spn> 可以在该 spn 上执行查找。  可能找不到该服务，或者可能已将其分配到 AD FS 服务帐户以外的其他帐户。

![综合性](media/ad-fs-tshoot-iwa/iwa3.png)

可以通过查看 AD FS 服务帐户的属性来验证 SPN。

![综合性](media/ad-fs-tshoot-iwa/iwa1.png)

## <a name="channel-binding-token"></a>通道绑定令牌
目前，当客户端应用程序通过 HTTPS 使用 Kerberos、Digest 或 NTLM 向服务器验证自身的身份时，首先会建立一个传输层安全 (TLS) 通道，然后使用此通道进行身份验证。

通道绑定令牌是 TLS 保护的外部通道的属性，用于通过客户端身份验证的内部通道将外部通道绑定到会话。

如果发生 "中间人" 攻击，并对 SSL 流量进行 crypting 和重新加密，则密钥将不会匹配（& a）。  AD FS 将确定在 web 浏览 r 和自身之间中间有一些东西。  这将导致 Kerberos 身份验证失败，并且系统会提示用户提供401对话框，而不是 SSO 体验。

这可能是由以下原因引起的：
 - 浏览器与 AD FS 中的任何内容
 - Fiddler
 - 执行 SSL 桥接的反向代理

默认情况下，AD FS 将此设置为 "允许"。  可以使用 PowerShell cmdlt 更改此设置`Set-ADFSProperties -ExtendProtectionTokenCheck`

有关详细信息，请参阅[安全规划和部署 AD FS 的最佳实践](../../ad-fs/design/best-practices-for-secure-planning-and-deployment-of-ad-fs.md)。

## <a name="internet-explorer-configuration"></a>Internet Explorer 配置
默认情况下，Internet explorer 将具有以下方法：

1. Internet explorer 将接收来自标头中的 "协商" AD FS 的401响应。
2. 这会告知 web 浏览器将 Kerberos 或 NTLM 票证发送回 AD FS。
3. 默认情况下，IE 将尝试执行此操作 (如果在标头中的 "协商") ，则无需用户交互。  它仅适用于 intranet 站点。

有2个主要功能会阻止 happeing。
   - 不会在 IE 的属性中检查启用集成 Windows 身份验证。  这位于 "Internet 选项" 下-> 高级-> 安全性。

   ![综合性](media/ad-fs-tshoot-iwa/iwa4.png)

   - 安全区域配置不正确
       - Fqdn 不在 intranet 区域中
       - AD FS URL 不在 intranet 区域中。

      ![综合性](media/ad-fs-tshoot-iwa/iwa5.png)
## <a name="next-steps"></a>后续步骤

- [AD FS 疑难解答](ad-fs-tshoot-overview.md)
