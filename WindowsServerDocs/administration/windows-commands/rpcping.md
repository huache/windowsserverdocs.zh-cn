---
title: rpcping
description: Rpcping 命令的参考文章，可确认运行 Microsoft Exchange Server 的计算机与网络上任何受支持的 Microsoft Exchange 客户端工作站之间的 RPC 连接。
ms.topic: reference
ms.assetid: 7382aa0d-90fc-47c0-84b3-15f52dd656d0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7351195d8206cb13b334ca3e06ffb794e4a13461
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641175"
---
# <a name="rpcping"></a>rpcping

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

确认运行 Microsoft Exchange Server 的计算机与网络上任何受支持的 Microsoft Exchange 客户端工作站之间的 RPC 连接。 此实用程序可用于检查 Microsoft Exchange Server 服务是否通过网络响应来自客户端工作站的 RPC 请求。

## <a name="syntax"></a>语法

```
rpcping [/t <protseq>] [/s <server_addr>] [/e <endpoint>
        |/f <interface UUID>[,majorver]] [/O <interface object UUID]
        [/i <#_iterations>] [/u <security_package_id>] [/a <authn_level>]
        [/N <server_princ_name>] [/I <auth_identity>] [/C <capabilities>]
        [/T <identity_tracking>] [/M <impersonation_type>]
        [/S <server_sid>] [/P <proxy_auth_identity>] [/F <RPCHTTP_flags>]
        [/H <RPC/HTTP_authn_schemes>] [/o <binding_options>]
        [/B <server_certificate_subject>] [/b] [/E] [/q] [/c]
        [/A <http_proxy_auth_identity>] [/U <HTTP_proxy_authn_schemes>]
        [/r <report_results_interval>] [/v <verbose_level>] [/d]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /t `<protseq>` | 指定要使用的协议顺序。 可以是标准 RPC 协议序列之一： ncacn_ip_tcp、ncacn_np 或 ncacn_http。<p>如果未指定，则默认值为 ncacn_ip_tcp。 |
| /s `<server_addr>` | 指定服务器地址。 如果未指定，则将 ping 本地计算机。 |
| /e `<endpoint>` | 指定要 ping 的终结点。 如果未指定任何内容，则将 ping 目标计算机上的终结点映射器。<p>此选项与接口 (**/f**) 选项互斥。 |
| /o `<binding_options>` | 指定 RPC ping 的绑定选项。 |
| /f `<interface UUID>[,Majorver]` | 指定要进行 ping 操作的接口。 此选项与 "终结点" 选项互斥。 接口指定为 UUID。<p>如果未指定 *majorver* ，则将查找接口版本1。<p>指定 interface 后， **rpcping** 将查询目标计算机上的终结点映射器以检索指定接口的终结点。 将使用命令行中指定的选项查询终结点映射器。 |
| /O `<object UUID>` | 如果接口已注册，则指定对象 UUID。 |
| /i `<#_iterations>` | 指定要进行的调用数。 默认值为 1。 如果指定了多个迭代，则此选项对于测量连接延迟非常有用。 |
| /u `<security_package_id>` | 指定 (安全提供程序) RPC 将用来进行调用的安全包。 安全包被标识为数字或名称。 如果使用数字，则该数字与 RpcBindingSetAuthInfoEx API 中的数字相同。 如果指定此选项，则必须指定除 " *无*" 之外的身份验证级别。 此选项没有默认值。 如果未指定，则 RPC 不会使用 ping 的安全性。 下面的列表显示了名称和数字。 名称不区分大小写：<ul><li>Negotiate/9 或 nego、snego 或 negotiate 之一</li><li>NTLM/10 或 NTLM</li><li>SChannel/14 或 SChannel</li><li>Kerberos/16 或 Kerberos</li><li>内核/20 或内核</li></ul> |
| /a `<authn_level>` | 指定要使用的身份验证级别。 如果指定此选项，则还必须指定 (**/u**) 的安全程序包 ID。 如果未指定此选项，则 RPC 不会使用 ping 的安全性。 此选项没有默认值。 可能的值为：<ul><li>连接</li><li>call</li><li>pkt</li><li>完整性 (integrity)</li><li>privacy</li></ul> |
| /N `<server_princ_name>` | 指定服务器主体名称。<p>仅当选择了身份验证级别和安全包时，才能使用此字段。 |
| /I `<auth_identity>` | 允许您指定替代标识以连接到服务器。 标识采用 "用户"、"域" 和 "密码" 格式。 如果 "用户名"、"域" 或 "密码" 具有可通过 shell 解释的特殊字符，请将该标识用双引号引起来。 你可以指定 `\*` 而不是密码，而 RPC 会提示你输入密码，而无需在屏幕上回显密码。 如果未指定此字段，将使用登录用户的标识。<p>仅当选择了身份验证级别和安全包时，才能使用此字段。 |
| /C `<capabilities>` | 指定标志的十六进制位掩码。 仅当选择了身份验证级别和安全包时，才能使用此字段。 |
| /T `<identity_tracking>` | 指定静态或动态。 如果未指定，则动态为默认值。<p>仅当选择了身份验证级别和安全包时，才能使用此字段。 |
| 一样 `<impersonation_type>` | 指定匿名、标识、模拟或委托。 默认值为模拟。<p>仅当选择了身份验证级别和安全包时，才能使用此字段。 |
| /S `<server_sid>` | 指定服务器的预期 SID。<p>仅当选择了身份验证级别和安全包时，才能使用此字段。 |
| /P `<proxy_auth_identity>` | 指定要向 RPC/HTTP 代理进行身份验证的标识。 的格式与 **/i** 选项的格式相同。 若要使用此选项，必须指定 (**/u**) 、身份验证级别 (**/a**) 和身份验证方案 (**/h**) 的安全包。 |
| /F `<RPCHTTP_flags>` | 指定为 RPC/HTTP 前端身份验证传递的标志。 标志可以指定为数字，也可以指定当前识别的标志：<ul><li>使用 SSL/1 或 ssl 或 use_ssl</li><li>使用第一种身份验证方案/2 或第一种或 use_first</li></ul>若要使用此选项，必须指定 (**/u**) 和身份验证级别 (**/a**) 的安全包。 |
| /H `<RPC/HTTP_authn_schemes>` | 指定用于 RPC/HTTP 前端身份验证的身份验证方案。 此选项是用逗号分隔的数值或名称列表。 示例： Basic、NTLM。 识别的值是 (名称不区分大小写) ：<ul><li>Basic/1 或 Basic</li><li>NTLM/2 或 NTLM</li><li>Certificate/65536 或 Cert</li></ul><p>若要使用此选项，必须指定 (**/u**) 和身份验证级别 (**/a**) 的安全包。 |
| /B `<server_certificate_subject>` | 指定服务器证书主题。 若要使用此选项，必须使用 SSL。<p>若要使用此选项，必须指定 (**/u**) 和身份验证级别 (**/a**) 的安全包。 |
| /b | 从服务器发送的证书中检索服务器证书使用者，并将其打印到屏幕或日志文件。 仅当代理仅回显选项 (/E) 并且指定了使用 SSL 选项时有效。<p>若要使用此选项，必须指定 (**/u**) 和身份验证级别 (**/a**) 的安全包。 |
| /R | 指定 HTTP 代理。 如果 *没有*，则使用 RPC 代理。 值 *默认* 表示在客户端计算机中使用 IE 设置。 其他任何值都将被视为显式 HTTP 代理。 如果未指定此标志，则假定默认值为，即检查 IE 设置。 仅当启用了 **/e** (回响) 标志时，此标志才有效。 |
| /E | 仅将 ping 限制为 RPC/HTTP 代理。 Ping 未到达服务器。 尝试确定是否可访问 RPC/HTTP 代理时非常有用。 若要指定 HTTP 代理，请使用/R 标志。 如果在/o 标志中指定 HTTP 代理，则将忽略此选项。<p>若要使用此选项，必须指定 (**/u**) 和身份验证级别 (**/a**) 的安全包。 |
| /q | 指定安静模式。 不会发出除密码之外的任何提示。 假设 *Y* 响应所有查询。 请谨慎使用此选项。 |
| /c | 使用智能卡证书。 rpcping 将提示用户选择智能卡。 |
| /A | 指定用于对 HTTP 代理进行身份验证的标识。 的格式与/I 选项的格式相同。<p>若要使用此选项，必须 (/U) 、security package (**/u**) 和 authentication **level (指定** 身份验证方案才能使用此选项。 |
| /U | 指定用于 HTTP 代理身份验证的身份验证方案。 此选项是用逗号分隔的数值或名称列表。 示例： Basic、NTLM。 识别的值是 (名称不区分大小写) ：<ul><li>Basic/1 或 Basic</li><li>NTLM/2 或 NTLM</li></ul>若要使用此选项，必须指定 (**/u**) 和身份验证级别 (**/a**) 的安全包。 |
| /r | 如果指定了多个迭代，则此选项将使 **rpcping** 在上次调用后定期显示当前执行统计信息。 报表间隔以秒为单位。 默认为 15. |
| /v | 告诉 **rpcping** 如何生成输出。 默认值为 1。 2和3提供 **rpcping**的输出。 |
| /d | 启动 RPC 网络诊断 UI。 |
| /p | 指定在身份验证失败时提示输入凭据。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要查明是否可以访问通过 RPC/HTTP 连接的 Exchange 服务器，请键入：

```
rpcping /t ncacn_http /s exchange_server /o RpcProxy=front_end_proxy /P username,domain,* /H Basic /u NTLM /a connect /F 3
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
