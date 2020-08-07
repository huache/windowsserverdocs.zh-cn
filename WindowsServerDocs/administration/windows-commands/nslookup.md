---
title: nslookup
description: Nslookup 命令的参考文章，其中显示了可用于诊断域名系统 (DNS) 基础结构的信息。
ms.topic: article
ms.assetid: 41516932-7833-434a-aa92-b4cf0f9a7ef7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7d01f167a198803db269e97e806a6d2867074d60
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87885323"
---
# <a name="nslookup"></a>nslookup

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示可用于诊断域名系统 (DNS) 基础结构的信息。 使用此工具之前，应熟悉 DNS 的工作原理。 只有安装了 TCP/IP 协议，才能使用 nslookup 命令行工具。

Nslookup 命令行工具有两种模式：交互式和非交互式。

如果只需要查找一段数据，我们建议使用非交互模式。 对于第一个参数，键入要查找的计算机的名称或 IP 地址。 对于第二个参数，请键入 DNS 名称服务器的名称或 IP 地址。 如果省略第二个参数，则**nslookup**将使用默认 DNS 名称服务器。

如果需要查找多个数据片段，可以使用交互模式。 为第一个参数键入连字符 ( ) ，为第二个参数键入 DNS 名称服务器的名称或 IP 地址。 如果省略这两个参数，则该工具将使用默认 DNS 名称服务器。 使用交互模式时，可以执行以下操作：

- 通过按 CTRL + B，随时中断交互式命令。

- 退出，通过键入**exit**。

- 将内置命令视为计算机名称，并在其前面加上转义字符 (\) 。 无法识别的命令被解释为计算机名。

## <a name="syntax"></a>语法

```
nslookup [exit | finger | help | ls | lserver | root | server | set | view] [options]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| [nslookup 退出](nslookup-exit-command.md) | 退出 nslookup 命令行工具。 |
| [nslookup finger](nslookup-finger-command.md) | 与当前计算机上的 finger 服务器连接。 |
| [nslookup help](nslookup-help.md) | 显示子命令的简短摘要。 |
| [nslookup ls](nslookup-ls.md) | 列出 DNS 域的信息。 |
| [nslookup lserver](nslookup-lserver.md) | 将默认服务器更改为指定的 DNS 域。 |
| [nslookup root](nslookup-root.md) | 将默认服务器更改为 DNS 域名空间的根服务器的服务器。 |
| [nslookup server](nslookup-server.md) | 将默认服务器更改为指定的 DNS 域。 |
| [nslookup set](nslookup-set.md) | 更改影响查找功能的配置设置。 |
| [nslookup set all](nslookup-set-all.md) | 打印配置设置的当前值。 |
| [nslookup set class](nslookup-set-class.md) | 更改查询类。 类指定信息的协议组。 |
| [nslookup set d2](nslookup-set-d2.md) | 启用或禁用穷举调试模式。 打印每个数据包的所有字段。 |
| [nslookup set debug](nslookup-set-debug.md) | 启用或禁用调试模式。 |
| [nslookup set domain](nslookup-set-domain.md) | 将默认 DNS 域名改为指定的名称。 |
| [nslookup set port](nslookup-set-port.md) | 将默认的 TCP/UDP DNS 名称服务器端口更改为指定值。 |
| [nslookup set querytype](nslookup-set-querytype.md) | 更改查询的资源记录类型。 |
| [nslookup set recurse](nslookup-set-recurse.md) | 告知 DNS 名称服务器在不包含信息的情况查询其他服务器。 |
| [nslookup set retry](nslookup-set-retry.md) | 设置重试次数。 |
| [nslookup set root](nslookup-set-root.md) | 更改用于查询的根服务器的名称。 |
| [nslookup set search](nslookup-set-search.md) | 向请求追加 dns 域搜索列表中的 DNS 域名，直到收到答案。 这适用于以下情况：集和查找请求至少包含一个句点，但不以尾随句点结束。 |
| [nslookup set srchlist](nslookup-set-srchlist.md) | 更改默认 DNS 域名和搜索列表。 |
| [nslookup set timeout](nslookup-set-timeout.md) | 更改等待答复请求的初始秒数。 |
| [nslookup set type](nslookup-set-type.md) | 更改查询的资源记录类型。 |
| [nslookup set vc](nslookup-set-vc.md) | 指定在向服务器发送请求时使用或不使用虚拟线路。 |
| [nslookup view](nslookup-view.md) | 排序并列出上一**ls**子命令或命令的输出。 |

### <a name="remarks"></a>备注

- 如果*computerTofind*是 IP 地址，并且查询用于**A**或**PTR**资源记录类型，则返回该计算机的名称。

- 如果*computerTofind*是一个名称并且没有尾随句点，则会将默认 DNS 域名追加到该名称。 此行为取决于以下**set**子命令的状态： **domain**、 **srchlist**、 **bre-walkthrough-defname**和**search**。

- 如果键入连字符 (-) 而不是*computerTofind*，则命令提示符将更改为**nslookup**交互模式。

- 如果查找请求失败，则命令行工具将提供一条错误消息，其中包括：

  | 错误消息 | 说明 |
  | ------------- | ----------- |
  | 超时 |服务器在一段时间内未响应请求，并且有一定次数的重试。 可以用[nslookup set timeout](nslookup-set-timeout.md)命令设置超时期限。 可以用[nslookup set retry](nslookup-set-retry.md)命令设置重试次数。 |
  | 服务器无响应 | 服务器计算机上没有运行任何 DNS 名称服务器。 |
  | 无记录 | DNS 名称服务器没有计算机的当前查询类型的资源记录，但计算机名称有效。 查询类型是通过[nslookup set querytype](nslookup-set-querytype.md)命令指定的。 |
  | 域不存在 | 计算机或 DNS 域名不存在。 |
  | 连接被拒绝或网络无法访问 | 无法连接到 DNS 名称服务器或 finger 服务器。 此错误通常发生在**ls**和**finger**请求上。 |
  | 服务器故障 | DNS 名称服务器在其数据库中发现内部不一致，无法返回有效的答案。 |
  | 拒绝 | DNS 名称服务器拒绝为请求服务。 |
  | 格式错误 | DNS 名称服务器发现请求数据包的格式不正确。 这可能表示**nslookup**中存在错误。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
