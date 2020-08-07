---
title: ksetup
description: Ksetup 命令的参考文章，它执行与设置和维护 Kerberos 协议和密钥发行中心 (KDC) 以支持 Kerberos 领域相关的任务。
ms.topic: article
ms.assetid: 4e046f8a-811b-48dc-9a69-18d8e097f353
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fc51f90f553ea2478c0c8f78cf77f7373eb47d7f
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887673"
---
# <a name="ksetup"></a>ksetup

执行与设置和维护 Kerberos 协议和密钥发行中心 (KDC) 以支持 Kerberos 领域相关的任务。 具体而言，此命令用于：

- 更改用于查找 Kerberos 领域的计算机设置。 在非 Microsoft 的基于 Kerberos 的实现中，此信息通常保存在 Krb5.conf 文件中。 在 Windows Server 操作系统中，它保存在注册表中。 您可以使用此工具来修改这些设置。 工作站使用这些设置来查找 Kerberos 领域，并由域控制器用于查找跨领域信任关系的 Kerberos 领域。

- 如果计算机不是 Windows 域的成员，则将 Kerberos 安全支持提供程序 (SSP) 使用的注册表项初始化为 Kerberos 领域定位 KDC。 完成配置后，运行 Windows 操作系统的客户端计算机的用户可以登录到 Kerberos 领域中的帐户。

- 在注册表中搜索用户领域的域名，然后通过查询 DNS 服务器将该名称解析为 IP 地址。 Kerberos 协议可以使用 DNS 来仅使用领域名称查找 Kdc，但必须对其进行特殊配置。

## <a name="syntax"></a>语法

```
ksetup
[/setrealm <DNSdomainname>]
[/mapuser <principal> <account>]
[/addkdc <realmname> <KDCname>]
[/delkdc <realmname> <KDCname>]
[/addkpasswd <realmname> <KDCPasswordName>]
[/delkpasswd <realmname> <KDCPasswordName>]
[/server <servername>]
[/setcomputerpassword <password>]
[/removerealm <realmname>]
[/domain <domainname>]
[/changepassword <oldpassword> <newpassword>]
[/listrealmflags]
[/setrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/addrealmflags <realmname> [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/delrealmflags [sendaddress] [tcpsupported] [delegate] [ncsupported] [rc4]]
[/dumpstate]
[/addhosttorealmmap] <hostname> <realmname>]
[/delhosttorealmmap] <hostname> <realmname>]
[/setenctypeattr] <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
[/getenctypeattr] <domainname>
[/addenctypeattr] <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
[/delenctypeattr] <domainname>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| [ksetup setrealm](ksetup-setrealm.md) | 使此计算机成为 Kerberos 领域的成员。 |
| [ksetup addkdc](ksetup-addkdc.md) | 为给定领域定义 KDC 条目。 |
| [ksetup delkdc](ksetup-delkdc.md) | 删除领域的 KDC 条目。 |
| [ksetup addkpasswd](ksetup-addkpasswd.md) | 为某个领域添加 kpasswd 服务器地址。 |
| [ksetup delkpasswd](ksetup-delkpasswd.md) | 删除领域的 kpasswd 服务器地址。 |
| [ksetup server](ksetup-server.md) | 允许您指定要应用更改的 Windows 计算机的名称。 |
| [ksetup setcomputerpassword](ksetup-setcomputerpassword.md) | 设置计算机的域帐户 (或主机主体) 的密码。 |
| [ksetup removerealm](ksetup-removerealm.md) | 从注册表中删除指定领域的所有信息。 |
| [ksetup domain](ksetup-domain.md) | 如果 `<domainname>` **/domain**参数) 尚未设置，则允许你指定域 (。 |
| [ksetup changepassword](ksetup-changepassword.md) | 允许你使用 kpasswd 更改已登录用户的密码。 |
| [ksetup listrealmflags](ksetup-listrealmflags.md) | 列出**ksetup**可检测的可用领域标志。 |
| [ksetup setrealmflags](ksetup-setrealmflags.md) | 设置特定领域的领域标志。 |
| [ksetup addrealmflags](ksetup-addrealmflags.md) | 将其他领域标志添加到领域。 |
| [ksetup delrealmflags](ksetup-delrealmflags.md) | 删除领域中的领域标志。 |
| [ksetup dumpstate](ksetup-dumpstate.md) | 分析给定计算机上的 Kerberos 配置。 将主机添加到注册表的领域映射。 |
| [ksetup addhosttorealmmap](ksetup-addhosttorealmmap.md) | 添加用于将主机映射到 Kerberos 领域的注册表值。 |
| [ksetup delhosttorealmmap](ksetup-delhosttorealmmap.md) | 删除将主计算机映射到 Kerberos 领域的注册表值。 |
| [ksetup setenctypeattr](ksetup-setenctypeattr.md) | 设置域的一个或多个加密类型信任属性。 |
| [ksetup getenctypeattr](ksetup-getenctypeattr.md) | 获取域的加密类型信任属性。 |
| [ksetup addenctypeattr](ksetup-addenctypeattr.md) | 向域的 "加密类型" 信任属性添加加密类型。 |
| [ksetup delenctypeattr](ksetup-delenctypeattr.md) | 删除域的 "加密类型" 信任属性。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)