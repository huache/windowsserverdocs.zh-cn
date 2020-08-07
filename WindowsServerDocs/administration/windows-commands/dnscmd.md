---
title: dnscmd
description: 用于管理 DNS 服务器的命令行接口的 dnscmd 命令的参考文章。
ms.topic: article
ms.assetid: e7f31cb5-a426-4e25-b714-88712b8defd5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc034b86cc095b8bd23a8c0fd71f9da515474068
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890789"
---
# <a name="dnscmd"></a>Dnscmd

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

用于管理 DNS 服务器的命令行界面。 此实用程序在编写批处理文件脚本时非常有用，有助于自动执行日常 DNS 管理任务，或在网络中执行简单的无人参与安装和配置新的 DNS 服务器。

## <a name="syntax"></a>语法

```
dnscmd <servername> <command> [<command parameters>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<servername>` | 远程或本地 DNS 服务器的 IP 地址或主机名。 |

## <a name="dnscmd-ageallrecords-command"></a>dnscmd/ageallrecords 命令

为 DNS 服务器上指定区域或节点上的资源记录设置时间戳的当前时间。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /ageallrecords <zonename>[<nodename>] | [/tree]|[/f]
```

#### <a name="parameters"></a>参数

| 参数 | 描述 |
| ---------- | ----------- |
| `<servername>` | 指定管理员计划管理的 DNS 服务器，由 IP 地址、完全限定的域名 (FQDN) 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定区域的 FQDN。 |
| `<nodename>` | 使用以下内容指定区域中的特定节点或子树：<ul><li>**@** 对于根区域或 FQDN</li><li>节点的 FQDN (名称，句点 (。 ) ) </li><li>相对于区域根的名称的单个标签。</li></ul> |
| /tree | 指定所有子节点也接收时间戳。 |
| /f | 运行命令而不要求确认。 |

##### <a name="remarks"></a>备注

- **Ageallrecords**命令用于实现 dns 的当前版本和以前版本的 dns 之间的向后兼容性，在这种情况下，不支持老化和清理。 它将包含当前时间的时间戳添加到没有时间戳的资源记录，并将当前时间设置为具有时间戳的资源记录。

- 除非记录有时间戳，否则不会进行记录清理。 Name server (NS) 资源记录、授权机构开始 (SOA) 资源记录和 Windows Internet 名称服务 (WINS) 不会在清理过程中包含资源记录，即使**ageallrecords**命令运行，也不会进行时间戳。

- 除非为 DNS 服务器和区域启用了清理，否则此命令将失败。 有关如何为区域启用清理的信息，请参阅本文的命令语法中的**老化**参数 `dnscmd /config` 。

- 将时间戳添加到 DNS 资源记录，使其与 Windows Server 以外的操作系统上运行的 DNS 服务器不兼容。 使用**ageallrecords**命令添加的时间戳不能撤消。

- 如果未指定任何可选参数，则该命令将返回指定节点上的所有资源记录。 如果至少为一个可选参数指定了值，则**dnscmd**仅枚举与可选参数或参数中指定的一个或多个值相对应的资源记录。

### <a name="examples"></a>示例

[示例1：将时间戳的当前时间设置为资源记录](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-1-set-the-current-time-on-a-time-stamp-to-resource-records)

## <a name="dnscmd-clearcache-command"></a>dnscmd/clearcache 命令

清除指定的 DNS 服务器上的资源记录的 DNS 缓存内存。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /clearcache
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |

### <a name="example"></a>示例

```
dnscmd dnssvr1.contoso.com /clearcache
```

## <a name="dnscmd-config-command"></a>dnscmd/config 命令

更改 DNS 服务器和单个区域的注册表中的值。 此命令还会修改指定服务器的配置。 接受服务器级别和区域级别设置。

> [!CAUTION]
> 不要直接编辑注册表，除非没有替代方法。 注册表编辑器会绕过标准安全措施，同时允许可能降低性能的设置、损坏系统，甚至要求你重新安装 Windows。 可以通过使用控制面板中的 "程序" 或 "Microsoft 管理控制台 (mmc) 来安全地更改大多数注册表设置。 如果必须直接编辑注册表，请首先对其进行备份。 有关详细信息，请参阅注册表编辑器帮助。

### <a name="server-level-syntax"></a>服务器级语法

```
dnscmd [<servername>] /config <parameter>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定您计划管理的 DNS 服务器，由本地计算机语法、IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<parameter>` | 指定一个设置和一个值作为选项。 参数值使用以下语法：*参数*[*value*]。 |
| /addressanswerlimit`[0|5-28]` | 指定 DNS 服务器为响应查询而可以发送的主机记录的最大数目。 该值可以为零 (0) ，也可以介于5到28个记录之间。 默认值为零 (0)。 |
| /bindsecondaries`[0|1]` | 更改区域传送的格式，使其能够实现最大的压缩和效率。 接受以下值：<ul><li>**0** -使用最大压缩，并与 BIND 版本4.9.4 和更高版本兼容</li><li>**1** -仅将每条消息的一个资源记录发送到非 Microsoft DNS 服务器，并且与4.9.4 之前的绑定版本兼容。 这是默认设置。</li></ul> |
| /bootmethod`[0|1|2|3]` | 确定 DNS 服务器从中获取其配置信息的源。 接受以下值：<ul><li>**0** -清除配置信息的源。</li><li>**1** -从位于 DNS 目录的绑定文件加载， `%systemroot%\System32\DNS` 默认情况下为。</li><li>**2** -从注册表加载。</li><li>**3** -从 AD DS 和注册表加载。 这是默认设置。</li></ul> |
| /defaultagingstate`[0|1]` | 确定默认情况下是否对新创建的区域启用 DNS 清理功能。 接受以下值：<ul><li>**0** -禁用清理。 这是默认设置。</li><li>**1** -启用清理。</li></ul> |
| /defaultnorefreshinterval`[0x1-0xFFFFFFFF|0xA8]` | 设置动态更新记录不接受刷新的时间段。 服务器上的区域会自动继承此值。<p>若要更改默认值，请键入**0x1-0xffffffff**范围内的值。 服务器的默认值为**0xA8**。 |
| /defaultrefreshinterval`[0x1-0xFFFFFFFF|0xA8]` | 设置允许动态更新 DNS 记录的时间段。 服务器上的区域会自动继承此值。<p>若要更改默认值，请键入**0x1-0xffffffff**范围内的值。 服务器的默认值为**0xA8**。 |
| /disableautoreversezones`[0|1]` | 启用或禁用反向查找区域的自动创建。 反向查找区域提供 Internet 协议 (IP) 地址到 DNS 域名的解析。 接受以下值：<ul><li>**0** -启用自动创建反向查找区域。 这是默认设置。</li><li>**1** -禁用自动创建反向查找区域。</li></ul> |
| /disablensrecordsautocreation`[0|1]` | 指定 DNS 服务器是否自动创建它所承载的区域的名称服务器 (NS) 资源记录。 接受以下值：<ul><li>**0** -自动为 DNS 服务器托管的区域创建名称服务器 (NS) 资源记录。</li><li>**1** -不会自动为 DNS 服务器托管的区域 (NS) 资源记录创建名称服务器。</li></ul> |
| /dspollinginterval`[0-30]` | 指定 DNS 服务器轮询 AD DS active directory 集成区域中的更改的频率。 |
| /dstombstoneinterval`[1-30]` |AD DS 中保留已删除记录的时间长度（以秒为单位）。 |
| /ednscachetimeout`[3600-15724800]` | 指定缓存扩展 DNS (EDNS) 信息的秒数。 最小值为**3600**，最大值为**15724800**。 默认值为**604800**秒 (一周) 。 |
| /enableednsprobes`[0|1]` | 启用或禁用服务器以探测其他服务器，以确定它们是否支持 EDNS。 接受以下值：<ul><li>**0** -禁用对 EDNS 探测的活动支持。</li><li>**1** -启用对 EDNS 探测的活动支持。</li></ul> |
| /enablednssec`[0|1]` | 启用或禁用 (DNSSEC) 对 DNS 安全扩展插件的支持。 接受以下值：<ul><li>**0** -禁用 DNSSEC。</li><li>**1** -启用 DNSSEC。</li></ul> |
| /enableglobalnamessupport`[0|1]` | 启用或禁用对 GlobalNames 区域的支持。 GlobalNames 区域支持跨林解析单标签 DNS 名称。 接受以下值：<ul><li>**0** -禁用对 GlobalNames 区域的支持。 将此命令的值设置为0时，DNS 服务器服务不解析 GlobalNames 区域中的单标签名称。</li><li>**1** -启用对 GlobalNames 区域的支持。 将此命令的值设置为1时，DNS 服务器服务将解析 GlobalNames 区域中的单标签名称。</li></ul> |
| /enableglobalqueryblocklist`[0|1]` | 启用或禁用对列表中名称解析的全局查询阻止列表的支持。 默认情况下，当服务首次启动时，DNS 服务器服务将创建并启用全局查询阻止列表。 若要查看当前的全局查询块列表，请使用 dnscmd/info **/globalqueryblocklist**命令。 接受以下值：<ul><li>**0** -禁用对全局查询块列表的支持。 将此命令的值设置为0时，DNS 服务器服务将对阻止列表中的名称的查询做出响应。</li><li>**1** -支持全局查询阻止列表。 将此命令的值设置为1时，DNS 服务器服务不会响应对阻止列表中的名称的查询。</li></ul> |
| /eventloglevel`[0|1|2|4]` | 确定事件查看器的 DNS 服务器日志中记录的事件。 接受以下值：<ul><li>**0** -不记录任何事件。</li><li>**1** -仅记录错误。</li><li>**2** -仅记录错误和警告。</li><li>**4** -记录错误、警告和信息性事件。 这是默认设置。</li></ul> |
| /forwarddelegations`[0|1]` | 确定 DNS 服务器如何处理委托的子的查询。 这些查询可以发送到查询中引用的子，也可以发送到为 DNS 服务器命名的转发器列表。 设置中的条目仅在启用转发时使用。 接受以下值：<ul><li>**0** -自动将引用委托的子区域的查询发送到相应的子。 这是默认设置。</li><li>**1** -将引用委托的子的查询转发到现有转发器。</li></ul> |
| /forwardingtimeout`[<seconds>]` | 确定在尝试另一个转发器之前， (**0x1-0xffffffff**) DNS 服务器等待转发器响应多少秒。 默认值为**0x5**，即5秒。 |
| /globalneamesqueryorder`[0|1]` | 指定在解析名称时，DNS 服务器服务是否首先在 GlobalNames 区域或本地区域中查找。 接受以下值：<ul><li>**0** -DNS 服务器服务将尝试通过先查询 GlobalNames 区域来解析名称，然后再查询其具有权威的区域。</li><li>**1** -DNS 服务器服务将尝试通过先查询其权威的区域来解析名称，然后再查询 GlobalNames 区域。</li></ul> |
| /globalqueryblocklist`[[<name> [<name>]...]` | 用指定名称的列表替换当前的全局查询块列表。 如果未指定任何名称，则此命令将清除阻止列表。 默认情况下，全局查询块列表包含以下项：<ul><li>isatap</li><li>wpad</li></ul>当首次启动时，DNS 服务器服务可以删除其中一个或两个这两个名称，前提是在现有区域中查找这些名称。 |
| /isslave`[0|1]` | 确定当 DNS 服务器转发的查询未收到响应时，DNS 服务器的响应方式。 接受以下值：<ul><li>**0** -指定 DNS 服务器不是从属服务器。 如果转发器没有响应，则 DNS 服务器将尝试解析查询本身。 这是默认设置。</li><li>**1** -指定 DNS 服务器是从属服务器。 如果转发器没有响应，则 DNS 服务器将终止搜索，并向解析程序发送失败消息。</li></ul> |
| /localnetpriority`[0|1]` | 确定当 DNS 服务器具有相同名称的多个主机记录时返回主机记录的顺序。 接受以下值：<ul><li>**0** -按照 DNS 数据库中列出的顺序返回记录。</li><li>**1** -返回具有相似 IP 网络地址的记录。 这是默认设置。</li></ul> |
| /logfilemaxsize`[<size>]` | 指定 Dns .log 文件 (**0x10000-0xffffffff**) 的最大大小（以字节为单位）。 当文件达到其最大大小时，DNS 会覆盖最旧的事件。 默认大小为 " **0x400000 处**"， (MB) 为 4 mb。 |
| /logfilepath`[<path+logfilename>]` | 指定 Dns 日志文件的路径。 默认路径为 `%systemroot%\System32\Dns\Dns.log`。 您可以使用格式指定其他路径 `path+logfilename` 。 |
| /logipfilterlist`<IPaddress> [,<IPaddress>...]` | 指定在调试日志文件中记录哪些数据包。 条目是 IP 地址的列表。 仅记录传入和传出列表中 IP 地址的数据包。 |
| /loglevel`[<eventtype>]` | 确定在 Dns .log 文件中记录的事件类型。 每个事件类型都用十六进制数表示。 如果希望日志中有多个事件，请使用十六进制加法添加值，然后输入 sum。 接受以下值：<ul><li>**0x0** -DNS 服务器不创建日志。 这是默认条目。</li><li>**0x10** -记录查询和通知。</li><li>**0x20** -记录更新。</li><li>**0xFE** -记录 nonquery 的事务。</li><li>**0x100** -记录问题事务。</li><li>**0x200** -记录答案。</li><li>**0x1000** -记录发送数据包。</li><li>**0x2000** -日志接收数据包。</li><li>**0x4000** - (UDP) 数据包记录用户数据报协议。</li><li>**0x8000** -记录传输控制协议 (TCP) 数据包。</li><li>**0xffff** -记录所有数据包。</li><li>**0x10000** -记录 active directory 写入事务。</li><li>**0x20000** -记录 active directory 更新事务。</li><li>**0x1000000** -记录完整的数据包。</li><li>**0x80000000** -记录写入事务。</li><li></ul> |
| /maxcachesize | 指定 DNS 服务器的内存缓存的最大大小（kb (KB) ）。 |
| /maxcachettl`[<seconds>]` | 确定在缓存中保存记录 (**0x0-0xffffffff**) 的秒数。 如果使用了**0x0**设置，则 DNS 服务器不会缓存记录。 默认设置为**0x15180** (86400 秒或1天) 。 |
| /maxnegativecachettl`[<seconds>]` | 指定 (**0x1-0xffffffff**) 记录反向查询应答的条目保留在 DNS 缓存中的秒数。 默认设置为**0x384** (900 秒) 。 |
| /namecheckflag`[0|1|2|3]` | 指定检查 DNS 名称时使用的字符标准。 接受以下值：<ul><li>**0** -使用符合 Internet 工程任务组 (IETF) 征求意见 (rfc) 的 ANSI 字符。</li><li>**1** -使用不一定符合 IETF RFC 的 ANSI 字符。</li><li>**2** -使用多字节 UCS 转换格式 8 (utf-8) 字符。 这是默认设置。</li><li>**3** -使用所有字符。</li></ul> |
| /norecursion`[0|1]` | 确定 DNS 服务器是否执行递归名称解析。 接受以下值：<ul><li>**0** -如果在查询中请求，则 DNS 服务器将执行递归名称解析。 这是默认设置。</li><li>**1** -DNS 服务器不执行递归名称解析。</li></ul> |
| /notcp | 此参数已过时，并且它在当前版本的 Windows Server 中不起作用。 |
| /recursionretry`[<seconds>]` | 确定 DNS 服务器在尝试联系远程服务器之前等待的秒数 (**0x1-0xffffffff**) 。 默认设置为**0x3** (三秒) 。 在慢速广域网上进行递归时，此值应增加 (WAN) 链接。 |
| /recursiontimeout`[<seconds>]` | 确定 DNS 服务器在停止尝试联系远程服务器之前等待的秒数 (**0x1-0xffffffff**) 。 设置范围为**0x1**到**0xffffffff**。 默认设置为**0xF**)  (15 秒。 如果递归发生在慢速 WAN 链接上，则应增加此值。 |
| /roundrobin`[0|1]` | 确定当服务器具有同一名称的多个主机记录时返回主机记录的顺序。 接受以下值：<ul><li>**0** -DNS 服务器不使用轮循机制。 而是返回每个查询的第一条记录。</li><li>**1** -DNS 服务器在其从顶部到匹配记录列表底部的记录之间进行旋转。 这是默认设置。</li></ul> |
| /rpcprotocol`[0x0|0x1|0x2|0x4|0xFFFFFFFF]` | 指定远程过程调用 (RPC) 在与 DNS 服务器建立连接时使用的协议。 接受以下值：<ul><li>**0x0** -禁用 DNS 的 RPC。</li><li>**0x01** -使用 tcp/ip</li><li>**0x2** -使用命名管道。</li><li>**0x4** -使用本地过程调用 (LPC) 。</li><li>**0xffffffff** -所有协议。 这是默认设置。</li></ul> |
| /scavenginginterval`[<hours>]` | 确定是否已启用 DNS 服务器的清理功能，并设置清理周期之间 (**0x0-0xffffffff**) 的小时数。 默认设置为**0x0**，这将禁用 DNS 服务器的清理。 设置大于**0x0**会启用对服务器的清理，并设置清理周期之间的小时数。 |
| /secureresponses`[0|1]` | 确定 DNS 是否筛选保存在缓存中的记录。 接受以下值：<ul><li>**0** -将对名称查询的所有响应保存到缓存中。 这是默认设置。</li><li>**1** -仅将属于同一 DNS 子树的记录保存到缓存中。</li></ul> |
| /sendport`[<port>]` | 指定 DNS 用于向其他 DNS 服务器发送递归查询 (**0x0-0xffffffff**) 的端口号。 默认设置为**0x0**，这意味着端口号是随机选择的。 |
| /serverlevelplugindll`[<dllpath>]` | 指定自定义插件的路径。 当 Dllpath 指定有效 DNS 服务器插件的完全限定路径名称时，DNS 服务器将在插件中调用函数，以解析超出所有本地托管区域的名称查询。 如果查询的名称超出了插件的作用域，则 DNS 服务器会根据配置使用转发或递归执行名称解析。 如果未指定 Dllpath，则在以前配置自定义插件时，DNS 服务器将停止使用自定义插件。 |
| /strictfileparsing`[0|1]` | 确定加载区域时遇到错误记录时 DNS 服务器的行为。 接受以下值：<ul><li>**0** -即使服务器遇到错误记录，DNS 服务器仍将继续加载该区域。 错误记录在 DNS 日志中。 这是默认设置。</li><li>**1** -dns 服务器停止加载区域，并在 DNS 日志中记录该错误。</li></ul> |
| /updateoptions`<RecordValue>` | 禁止动态更新指定类型的记录。 如果要在日志中禁止多个记录类型，请使用十六进制加法添加值，然后输入和。 接受以下值：<ul><li>**0x0** -不限制任何记录类型。</li><li>**0x1** -不包括开始 (SOA) 资源记录的授权。</li><li>**0x2** -排除 name SERVER (NS) 资源记录。</li><li>**0x4** -排除 name SERVER (NS) 资源记录的委托。</li><li>**0x8** -排除服务器主机记录。</li><li>**0x100** -在安全动态更新期间，不包括 (SOA) 资源记录的启动颁发机构。</li><li>**0x200** -在安全动态更新期间，不包括根名称服务器 (NS) 资源记录。</li><li>**0x30F** -在标准动态更新期间，不包括 name SERVER (NS) 资源记录、授权开始 (SOA) 资源记录和服务器主机记录。 在安全动态更新期间，不包括根名称服务器 (NS) 资源记录和授权 (SOA) 资源记录。 允许委托和服务器主机更新。</li><li>**0x400** -在安全动态更新期间，不包括) 资源记录 (NS 的委派名称服务器。</li><li>**0x800** -在安全动态更新期间，不包括服务器主机记录。</li><li>**0x1000000** - (DS) 记录中排除委托签名程序。</li><li>**0x80000000** -禁用 DNS 动态更新。</li></ul> |
| /writeauthorityns`[0|1]` | 确定 DNS 服务器何时在响应的 "授权" 部分中将名称服务器 (NS 写入) 资源记录。 接受以下值：<ul><li>**0** - (NS 写入名称服务器) 资源记录。 此设置符合 Rfc 1034、域名概念和设施以及 Rfc 2181，并向 DNS 规范进行说明。 这是默认设置。</li><li>**1** -在所有成功的权威响应的 "授权" 部分中写入名称服务器 (NS) 资源记录。</li></ul> |
| /xfrconnecttimeout`[<seconds>]` | 确定主 DNS 服务器等待其辅助服务器的传输响应 (**0x0-0xffffffff**) 的秒数。 默认值为**0x1E** (30 秒) 。 超时值过期后，连接将终止。 |

### <a name="zone-level-syntax"></a>区域级别的语法

修改指定区域的配置。 只能为区域级别参数指定区域名称。

```
dnscmd /config <parameters>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<parameter>` | 指定一个设置、一个区域名称和一个值作为选项。 参数值使用以下语法： `zonename parameter [value]` 。 |
| /aging`<zonename>`| 启用或禁用特定区域中的清理。 |
| /allownsrecordsautocreation `<zonename>``[value]` | 覆盖 DNS 服务器的名称服务器 (NS) resource record 启用设置。 之前为此区域注册 (NS) 资源记录的名称服务器不受影响。 因此，你必须手动将其删除（如果不希望这样做）。 |
| /allowupdate`<zonename>` | 确定指定区域是否接受动态更新。 |
| /forwarderslave`<zonename>` | 替代 DNS 服务器 **/isslave**设置。 |
| /forwardertimeout`<zonename>` | 确定在尝试另一个转发器之前 DNS 区域等待转发器响应的秒数。 此值将覆盖在服务器级别设置的值。 |
| /norefreshinterval`<zonename>` | 设置区域的时间间隔，在此时间间隔内，无刷新可以动态更新指定区域中的 DNS 记录。 |
| /refreshinterval`<zonename>` | 设置区域的时间间隔，在此时间间隔内刷新可以动态更新指定区域中的 DNS 记录。 |
| /securesecondaries`<zonename>` | 确定哪些辅助服务器可以从该区域的主服务器接收区域更新。 |

## <a name="dnscmd-createbuiltindirectorypartitions-command"></a>dnscmd/createbuiltindirectorypartitions 命令

创建 DNS 应用程序目录分区。 安装 DNS 时，将在林和域级别创建该服务的应用程序目录分区。 使用此命令创建已删除或从未创建的 DNS 应用程序目录分区。 如果没有参数，此命令将为域创建内置 DNS 目录分区。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /createbuiltindirectorypartitions [/forest] [/alldomains]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| /forest | 为林创建 DNS 目录分区。 |
| /alldomains | 为林中的所有域创建 DNS 分区。 |

## <a name="dnscmd-createdirectorypartition-command"></a>dnscmd/createdirectorypartition 命令

创建 DNS 应用程序目录分区。 安装 DNS 时，将在林和域级别创建该服务的应用程序目录分区。 此操作创建其他 DNS 应用程序目录分区。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /createdirectorypartition <partitionFQDN>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<partitionFQDN>` | 要创建的 DNS 应用程序目录分区的 FQDN。 |

## <a name="dnscmd-deletedirectorypartition-command"></a>dnscmd/deletedirectorypartition 命令

删除现有的 DNS 应用程序目录分区。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /deletedirectorypartition <partitionFQDN>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<partitionFQDN>` | 将删除的 DNS 应用程序目录分区的 FQDN。 |

## <a name="dnscmd-directorypartitioninfo-command"></a>dnscmd/directorypartitioninfo 命令

列出有关指定的 DNS 应用程序目录分区的信息。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /directorypartitioninfo <partitionFQDN> [/detail]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<partitionFQDN>` | DNS 应用程序目录分区的 FQDN。 |
| /detail | 列出有关应用程序目录分区的所有信息。 |

## <a name="dnscmd-enlistdirectorypartition-command"></a>dnscmd/enlistdirectorypartition 命令

将 DNS 服务器添加到指定的目录分区的副本集。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /enlistdirectorypartition <partitionFQDN>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<partitionFQDN>` | DNS 应用程序目录分区的 FQDN。 |

## <a name="dnscmd-enumdirectorypartitions-command"></a>dnscmd/enumdirectorypartitions 命令

列出指定服务器的 DNS 应用程序目录分区。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /enumdirectorypartitions [/custom]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| /custom | 仅列出用户创建的目录分区。 |

## <a name="dnscmd-enumrecords-command"></a>dnscmd/enumrecords 命令

列出 DNS 区域中指定节点的资源记录。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /enumrecords <zonename> <nodename> [/type <rrtype> <rrdata>] [/authority] [/glue] [/additional] [/node | /child | /startchild<childname>] [/continue | /detail]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| /enumrecords | 列出指定区域中的资源记录。 |
| `<zonename>` | 指定资源记录所属的区域的名称。 |
| `<nodename>` | 指定资源记录的节点名称。 |
| `[/type <rrtype> <rrdata>]` | 指定要列出的资源记录的类型以及所需的数据类型。 接受以下值：<ul><li>`<rrtype>`-指定要列出的资源记录的类型。</li><li>`<rrdata>`-指定所需的数据类型。</li></ul> |
| /authority | 包括权威数据。 |
| /glue | 包括粘附数据。 |
| /additional | 包括有关列出的资源记录的所有其他信息。 |
| /node | 仅列出指定节点的资源记录。 |
| /child | 仅列出指定子域的资源记录。 |
| /startchild`<childname>` | 从指定的子域开始列表。 |
| /continue | 仅列出具有其类型和数据的资源记录。 |
| /detail | 列出有关资源记录的所有信息。 |

#### <a name="example"></a>示例

```
dnscmd /enumrecords test.contoso.com test /additional
```

## <a name="dnscmd-enumzones-command"></a>dnscmd/enumzones 命令

列出指定的 DNS 服务器上存在的区域。 **Enumzones**参数充当区域列表的筛选器。 如果未指定任何筛选器，则返回区域的完整列表。 指定筛选器后，只会在返回的区域列表中包含满足筛选条件的区域。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /enumzones [/primary | /secondary | /forwarder | /stub | /cache | /auto-created] [/forward | /reverse | /ds | /file] [/domaindirectorypartition | /forestdirectorypartition | /customdirectorypartition | /legacydirectorypartition | /directorypartition <partitionFQDN>]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| /primary | 列出属于标准主要区域或 active directory 集成区域的所有区域。 |
| /secondary | 列出所有标准辅助区域。 |
| /forwarder | 列出将未解析的查询转发到另一台 DNS 服务器的区域。 |
| /stub | 列出所有存根区域。 |
| /cache | 仅列出加载到缓存中的区域。 |
| /auto-created] | 列出在 DNS 服务器安装过程中自动创建的区域。 |
| /forward | 列出正向查找区域。 |
| 反向 | 列出反向查找区域。 |
| /ds | 列出 active directory 集成区域。 |
| /file | 列出由文件支持的区域。 |
| /domaindirectorypartition | 列出域目录分区中存储的区域。 |
| /forestdirectorypartition | 列出林 DNS 应用程序目录分区中存储的区域。 |
| /customdirectorypartition | 列出用户定义的应用程序目录分区中存储的所有区域。 |
| /legacydirectorypartition | 列出域目录分区中存储的所有区域。 |
| /directorypartition`<partitionFQDN>` | 列出指定目录分区中存储的所有区域。 |

#### <a name="examples"></a>示例

- [示例2：显示 DNS 服务器上的完整区域列表](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-2-display-a-complete-list-of-zones-on-a-dns-server)) 

- [示例3：在 DNS 服务器上显示由区域的列表](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-3-display-a-list-of-autocreated-zones-on-a-dns-server)

## <a name="dnscmd-exportsettings-command"></a>dnscmd/exportsettings 命令

创建一个文本文件，该文件列出 DNS 服务器的配置详细信息。 文本文件命名为*DnsSettings.txt*。 它位于 `%systemroot%\system32\dns` 服务器的目录中。 你可以使用**dnscmd/exportsettings**创建的文件中的信息来解决配置问题，或者确保配置了多个相同的服务器。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /exportsettings
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |

## <a name="dnscmd-info-command"></a>dnscmd/info 命令

显示指定服务器的注册表的 DNS 部分中的设置 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DNS\Parameters` 。 若要显示区域级别的注册表设置，请使用 `dnscmd zoneinfo` 命令。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /info [<settings>]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<settings>` | **信息**命令返回的任何设置都可以单独指定。 如果未指定设置，则返回常见设置的报表。 |

#### <a name="example"></a>示例

- [示例4：显示 DNS 服务器的 IsSlave 设置](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-4-display-the-isslave-setting-from-a-dns-server)

- [示例5：显示 DNS 服务器的 RecursionTimeout 设置](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-5-display-the-recursiontimeout-setting-from-a-dns-server)

## <a name="dnscmd-ipvalidate-command"></a>dnscmd/ipvalidate 命令

测试 IP 地址是标识正常运行的 DNS 服务器，还是 DNS 服务器可以充当转发器、根提示服务器或特定区域的主服务器。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /ipvalidate <context> [<zonename>] [[<IPaddress>]]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<context>` | 指定要执行的测试类型。 可以指定以下任意测试：<ul><li>**/dnsservers** -测试具有指定地址的计算机是否运行 DNS 服务器。</li><li>**/forwarders** -测试指定的地址是否可识别可充当转发器的 DNS 服务器。</li><li>**/roothints** -测试指定的地址是否可识别可充当根提示名称服务器的 DNS 服务器。</li><li>**/zonemasters** -测试指定的地址是否识别作为*zonename*的主服务器的 DNS 服务器。 |
| `<zonename>` | 标识区域。 将此参数与 **/zonemasters**参数一起使用。 |
| `<IPaddress>` | 指定命令测试的 IP 地址。 |

#### <a name="examples"></a>示例

```
nscmd dnssvr1.contoso.com /ipvalidate /dnsservers 10.0.0.1 10.0.0.2
dnscmd dnssvr1.contoso.com /ipvalidate /zonemasters corp.contoso.com 10.0.0.2
```

## <a name="dnscmd-nodedelete-command"></a>dnscmd/nodedelete 命令

删除指定主机的所有记录。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /nodedelete <zonename> <nodename> [/tree] [/f]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定区域的名称。 |
| `<nodename>` | 指定要删除的节点的主机名。 |
| /tree | 删除所有子记录。 |
| /f | 执行命令而不要求确认。 |

#### <a name="example"></a>示例

[示例6：从节点中删除记录](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-6-delete-the-records-from-a-node)

## <a name="dnscmd-recordadd-command"></a>dnscmd/recordadd 命令

将记录添加到 DNS 服务器中的指定区域。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /recordadd <zonename> <nodename> <rrtype> <rrdata>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定记录所在的区域。 |
| `<nodename>` | 指定区域中的特定节点。 |
| `<rrtype>` | 指定要添加的记录的类型。 |
| `<rrdata>` | 指定预期的数据类型。 |

> [!NOTE]
> 添加记录后，请确保使用正确的数据类型和数据格式。 有关资源记录类型和相应数据类型的列表，请参阅[Dnscmd 示例](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10))。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /recordadd test A 10.0.0.5
dnscmd /recordadd test.contoso.com test MX 10 mailserver.test.contoso.com
```

## <a name="dnscmd-recorddelete-command"></a>dnscmd/recorddelete 命令

删除指定区域中的资源记录。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /recorddelete <zonename> <nodename> <rrtype> <rrdata> [/f]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定资源记录所在的区域。 |
| `<nodename>` | 指定主机的名称。 |
| `<rrtype>` | 指定要删除的资源记录的类型。 |
| `<rrdata>` | 指定预期的数据类型。 |
| /f | 执行命令而不要求确认。 由于节点可以有多个资源记录，因此此命令要求您非常具体地了解要删除的资源记录类型。 如果指定了数据类型，但未指定资源记录数据的类型，则会删除具有指定节点的特定数据类型的所有记录。 |

#### <a name="examples"></a>示例

```
dnscmd /recorddelete test.contoso.com test MX 10 mailserver.test.contoso.com
```

## <a name="dnscmd-resetforwarders-command"></a>dnscmd/resetforwarders 命令

选择或重置 DNS 服务器在本地无法解析 DNS 查询时将其转发到的 IP 地址。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /resetforwarders <IPaddress> [,<IPaddress>]...][/timeout <timeout>] [/slave | /noslave]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<IPaddress>` | 列出 DNS 服务器将未解析的查询转发到的 IP 地址。 |
| /timeout`<timeout>` | 设置 DNS 服务器等待转发器响应的秒数。 默认情况下，此值为5秒。 |
| /slave | 如果转发器未能解析查询，则阻止 DNS 服务器执行其自身的迭代查询。 |
| /noslave | 如果转发器未能解析查询，则允许 DNS 服务器执行其自身的迭代查询。 这是默认设置。 |
| /f | 执行命令而不要求确认。 由于节点可以有多个资源记录，因此此命令要求您非常具体地了解要删除的资源记录类型。 如果指定了数据类型，但未指定资源记录数据的类型，则会删除具有指定节点的特定数据类型的所有记录。 |

##### <a name="remarks"></a>备注

- 默认情况下，DNS 服务器在无法解析查询时执行迭代查询。

- 使用**resetforwarders**命令设置 IP 地址会使 dns 服务器对指定 IP 地址的 dns 服务器执行递归查询。 如果转发器未解析查询，则 DNS 服务器可以执行其自己的迭代查询。

- 如果使用 **/slave**参数，则 DNS 服务器不会执行其自己的迭代查询。 这意味着，DNS 服务器仅将未解析的查询转发到列表中的 DNS 服务器，并且，如果转发器没有解决这些查询，则不会尝试迭代查询。 将一个 IP 地址设置为 DNS 服务器的转发器会更有效。 你可以对网络中的内部服务器使用**resetforwarders**命令，将未解析的查询转发到一个具有外部连接的 DNS 服务器。

- 列出转发器的 IP 地址两次会导致 DNS 服务器尝试转发到该服务器两次。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /resetforwarders 10.0.0.1 /timeout 7 /slave
dnscmd dnssvr1.contoso.com /resetforwarders /noslave
```

## <a name="dnscmd-resetlistenaddresses-command"></a>dnscmd/resetlistenaddresses 命令

指定服务器上侦听 DNS 客户端请求的 IP 地址。 默认情况下，DNS 服务器上的所有 IP 地址都侦听客户端 DNS 请求。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /resetlistenaddresses <listenaddress>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<listenaddress>` | 指定 DNS 服务器上侦听 DNS 客户端请求的 IP 地址。 如果未指定侦听地址，则服务器上的所有 IP 地址将侦听客户端请求。 |

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /resetlistenaddresses 10.0.0.1
```

## <a name="dnscmd-startscavenging-command"></a>dnscmd/startscavenging 命令

通知 DNS 服务器尝试立即搜索指定 DNS 服务器中的过时资源记录。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /startscavenging
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |

##### <a name="remarks"></a>备注

- 此命令成功完成后会立即开始清除。 如果清除失败，则不会显示任何警告消息。

- 尽管开始清除的命令似乎已成功完成，但清除不会启动，除非满足以下前提条件：

    - 同时为服务器和区域启用了清理。

    - 区域已启动。

    - 资源记录有时间戳。

- 有关如何为服务器启用清理的信息，请参阅 **/config**部分**服务器级语法**下的**scavenginginterval**参数。

- 有关如何为区域启用清理的信息，请参阅 **/config**部分的**区域级语法**下的**老化**参数。

- 有关如何重新启动已暂停区域的信息，请参阅本文中的**zoneresume**参数。

- 有关如何检查时间戳的资源记录的信息，请参阅本文中的**ageallrecords**参数。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /startscavenging
```

## <a name="dnscmd-statistics-command"></a>dnscmd/statistics 命令

显示或清除指定 DNS 服务器的数据。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /statistics [<statid>] [/clear]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<statid>` | 指定要显示的统计信息或统计组合。 **Statistics**命令显示启动或恢复 DNS 服务器时开始的计数器。 标识号用于标识统计信息。 如果未指定统计信息 ID 号，则显示所有统计信息。 可以指定的数字以及显示的相应统计信息可包括：<ul><li>**00000001** -时间</li><li>**00000002** -查询</li><li>**00000004** -Query2</li><li>**00000008** -递归</li><li>**00000010** -Master</li><li>**00000020** -辅助</li><li>**00000040** -WINS</li><li>**00000100** -更新</li><li>**00000200** -SkwanSec</li><li>**00000400** -Ds</li><li>**00010000** -内存</li><li>**00100000** -PacketMem</li><li>**00040000** -Dbase</li><li>**00080000** -记录</li><li>**00200000** -NbstatMem</li><li>**/clear** -将指定的统计信息计数器重置为零。</li></ul> |

#### <a name="examples"></a>示例

- [示例7：](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-7-display-time-statistics-for-a-dns-server)

- [示例8：显示 DNS 服务器的 NbstatMem 统计信息](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-8-display-nbstatmem-statistics-for-a-dns-server)

## <a name="dnscmd-unenlistdirectorypartition-command"></a>dnscmd/unenlistdirectorypartition 命令

从指定的目录分区的副本集中删除 DNS 服务器。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /unenlistdirectorypartition <partitionFQDN>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<partitionFQDN>` | 将删除的 DNS 应用程序目录分区的 FQDN。 |

## <a name="dnscmd-writebackfiles-command"></a>dnscmd/writebackfiles 命令

检查 DNS 服务器内存的更改，并将其写入永久性存储。 **Writebackfiles**命令将更新所有脏区域或指定的区域。 如果内存中有任何尚未写入持久存储的更改，则区域会变脏。 这是一个用于检查所有区域的服务器级操作。 可以在此操作中指定一个区域，也可以使用**zonewriteback**操作。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /writebackfiles <zonename>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要更新的区域的名称。 |

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /writebackfiles
```

## <a name="dnscmd-zoneadd-command"></a>dnscmd/zoneadd 命令

将区域添加到 DNS 服务器。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneadd <zonename> <zonetype> [/dp <FQDN> | {/domain | enterprise | legacy}]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定区域的名称。 |
| `<zonetype>` | 指定要创建的区域的类型。 指定区域类型 **/forwarder**或 **/dsforwarder**将创建执行条件转发的区域。 每个区域类型都具有不同的必需参数：<ul><li>**/dsprimary** -创建 active directory 集成区域。</li><li>**/primary/file `<filename>` **-创建标准主要区域，并指定将存储区域信息的文件的名称。</li><li>**/secondary `<masterIPaddress> [<masterIPaddress>...]` **-创建标准辅助区域。</li><li>**/stub `<masterIPaddress> [<masterIPaddress>...]` /File `<filename>` ** -创建支持文件的存根区域。</li><li>**/dsstub `<masterIPaddress> [<masterIPaddress>...]` **-创建 active directory 集成存根区域。</li><li>**/forwarder `<masterIPaddress> [<masterIPaddress>]` .../File `<filename>` ** -指定创建的区域将未解析的查询转发到另一台 DNS 服务器。</li><li>**/dsforwarder** -指定创建的 active directory 集成区域将未解析的查询转发到另一台 DNS 服务器。</li></ul> |
| `<FQDN>` | 指定目录分区的 FQDN。 |
| /domain | 在域目录分区上存储区域。 |
| /enterprise | 在企业目录分区上存储区域。 |
| /legacy | 将区域存储在旧目录分区上。 |

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zoneadd test.contoso.com /dsprimary
dnscmd dnssvr1.contoso.com /zoneadd secondtest.contoso.com /secondary 10.0.0.2
```

## <a name="dnscmd-zonechangedirectorypartition-command"></a>dnscmd/zonechangedirectorypartition 命令

更改指定区域所在的目录分区。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zonechangedirectorypartition <zonename> {[<newpartitionname>] | [<zonetype>]}
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 区域所在的当前目录分区的 FQDN。 |
| `<newpartitionname>` | 区域将移动到的目录分区的 FQDN。 |
| `<zonetype>` | 指定区域将移动到的目录分区类型。 |
| /domain | 将区域移动到内置域目录分区。 |
| /forest | 将区域移到内置的林目录分区。 |
| /legacy | 将区域移动到为 active directory 域控制器创建的目录分区。 这些目录分区并不是纯模式所必需的。 |

## <a name="dnscmd-zonedelete-command"></a>dnscmd/zonedelete 命令

删除指定的区域。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zonedelete <zonename> [/dsdel] [/f]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要删除的区域的名称。 |
| /dsdel | 从 Azure Directory 域服务 (AD DS) 中删除区域。 |
| /f | 运行命令而不要求确认。 |

#### <a name="examples"></a>示例

- [示例9：从 DNS 服务器中删除区域](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-9-delete-a-zone-from-a-dns-server)

## <a name="dnscmd-zoneexport-command"></a>dnscmd/zoneexport 命令

创建一个文本文件，该文件列出指定区域的资源记录。 **Zoneexport**操作为 active directory 集成区域创建一条资源记录文件，以便进行故障排除。 默认情况下，此命令创建的文件放置在 DNS 目录中，默认情况下，该目录为 `%systemroot%/System32/Dns` 目录。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneexport <zonename> <zoneexportfile>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定区域的名称。 |
| `<zoneexportfile>` | 指定要创建的文件的名称。 |

#### <a name="examples"></a>示例

- [示例10：将区域资源记录列表导出到文件](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-10-export-zone-resource-records-list-to-a-file)

## <a name="dnscmd-zoneinfo"></a>dnscmd/zoneinfo

显示指定区域的注册表部分的设置：`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\DNS\Parameters\Zones\<zonename>`

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneinfo <zonename> [<setting>]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定区域的名称。 |
| `<setting>` | 您可以单独指定**zoneinfo**命令返回的任何设置。 如果未指定设置，则返回所有设置。 |

##### <a name="remarks"></a>备注

- 若要显示服务器级注册表设置，请使用 **/info**命令。

- 若要查看可使用此命令显示的设置的列表，请参阅 **/config**命令。

#### <a name="examples"></a>示例

- [示例11：显示注册表中的 RefreshInterval 设置](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-11-display-refreshinterval-setting-from-the-registry)

- [示例12：显示注册表中的老化设置](/previous-versions/windows/it-pro/windows-server-2003/cc784399(v=ws.10)#example-12-display-aging-setting-from-the-registry)

## <a name="dnscmd-zonepause-command"></a>dnscmd/zonepause 命令

暂停指定的区域，后者将忽略查询请求。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zonepause <zonename>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要暂停的区域的名称。 |

##### <a name="remarks"></a>备注

- 若要恢复区域并使其在暂停后可用，请使用 **/zoneresume**命令。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zonepause test.contoso.com
```

## <a name="dnscmd-zoneprint-command"></a>dnscmd/zoneprint 命令

列出区域中的记录。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneprint <zonename>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要列出的区域的名称。 |







## <a name="dnscmd-zonerefresh-command"></a>dnscmd/zonerefresh 命令

强制从主区域更新辅助 DNS 区域。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zonerefresh <zonename>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要刷新的区域的名称。 |

##### <a name="remarks"></a>备注

- **Zonerefresh**命令强制检查主服务器启动颁发机构 (SOA) 资源记录中的版本号。 如果主服务器上的版本号高于辅助服务器的版本号，则会启动区域传送来更新辅助服务器。 如果版本号相同，则不会进行区域传输。

- 默认情况下，强制检查每15分钟发生一次。 若要更改默认设置，请使用 `dnscmd config refreshinterval` 命令。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zonerefresh test.contoso.com
```

## <a name="dnscmd-zonereload-command"></a>dnscmd/zonereload 命令

从源复制区域信息。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zonereload <zonename>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要重新加载的区域的名称。 |

##### <a name="remarks"></a>备注

- 如果区域是 active directory 集成的，则会从 Active Directory 域服务 (AD DS) 重新加载该区域。

- 如果该区域是一个标准的支持文件的区域，则会从文件重新加载。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zonereload test.contoso.com
```

## <a name="dnscmd-zoneresetmasters-command"></a>dnscmd/zoneresetmasters 命令

将提供区域传输信息的主服务器的 IP 地址重置为辅助区域。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneresetmasters <zonename> [/local] [<IPaddress> [<IPaddress>]...]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要重置的区域的名称。 |
| /local | 设置本地主列表。 此参数用于 active directory 集成区域。 |
| `<IPaddress>` | 辅助区域的主服务器的 IP 地址。 |

##### <a name="remarks"></a>备注

- 此值最初在创建辅助区域时设置。 在辅助服务器上使用**zoneresetmasters**命令。 如果在主 DNS 服务器上设置此值，则该值无效。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zoneresetmasters test.contoso.com 10.0.0.1
dnscmd dnssvr1.contoso.com /zoneresetmasters test.contoso.com /local
```

## <a name="dnscmd-zoneresetscavengeservers-command"></a>dnscmd/zoneresetscavengeservers 命令

更改可清理指定区域的服务器的 IP 地址。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneresetscavengeservers <zonename> [/local] [<IPaddress> [<IPaddress>]...]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要清除的区域。 |
| /local | 设置本地主列表。 此参数用于 active directory 集成区域。 |
| `<IPaddress>` | 列出可执行清理的服务器的 IP 地址。 如果省略此参数，则承载此区域的所有服务器都可以清理它。 |

##### <a name="remarks"></a>备注

- 默认情况下，托管区域的所有服务器都可以清理该区域。

- 如果区域托管在多个 DNS 服务器上，则可以使用此命令减少区域清理的次数。

- 对于受此命令影响的 DNS 服务器和区域，必须启用清理。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zoneresetscavengeservers test.contoso.com 10.0.0.1 10.0.0.2
```

## <a name="dnscmd-zoneresetsecondaries-command"></a>dnscmd/zoneresetsecondaries 命令

指定主服务器在请求区域传输时响应的辅助服务器的 IP 地址列表。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneresetsecondaries <zonename> {/noxfr | /nonsecure | /securens | /securelist <securityIPaddresses>} {/nonotify | /notify | /notifylist <notifyIPaddresses>}
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定将重置其辅助服务器的区域的名称。 |
| /local | 设置本地主列表。 此参数用于 active directory 集成区域。 |
| /noxfr | 指定不允许区域传输。 |
| /nonsecure | 指定授予所有区域传送请求。 |
| /securens | 指定仅为区域的名称服务器 (NS) 资源记录中列出的服务器授予传输。 |
| /securelist | 指定仅向服务器列表授予区域传输。 此参数必须后跟主服务器使用的一个或多个 IP 地址。 |
| `<securityIPaddresses>` | 列出从主服务器接收区域传送的 IP 地址。 此参数仅与 **/securelist**参数一起使用。 |
| /nonotify | 指定不将更改通知发送到辅助服务器。 |
| /notify | 指定将更改通知发送到所有辅助服务器。 |
| /notifylist | 指定仅将更改通知发送到服务器列表。 此命令后面必须跟有主服务器使用的一个或多个 IP 地址。 |
| `<notifyIPaddresses>` | 指定将更改通知发送到的一个或多个辅助服务器的 IP 地址。 此列表仅与 **/notifylist**参数一起使用。 |

##### <a name="remarks"></a>备注

- 使用主服务器上的**zoneresetsecondaries**命令指定其如何响应辅助服务器中的区域复制请求。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zoneresetsecondaries test.contoso.com /noxfr /nonotify
dnscmd dnssvr1.contoso.com /zoneresetsecondaries test.contoso.com /securelist 11.0.0.2
```

## <a name="dnscmd-zoneresettype-command"></a>dnscmd/zoneresettype 命令

更改区域的类型。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneresettype <zonename> <zonetype> [/overwrite_mem | /overwrite_ds]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 标识将更改类型的区域。 |
| `<zonetype>` | 指定要创建的区域的类型。 每种类型具有不同的必需参数，其中包括：<ul><li>**/dsprimary** -创建 active directory 集成区域。</li><li>**/primary/file `<filename>` **-创建标准主要区域。</li><li>**/secondary `<masterIPaddress> [,<masterIPaddress>...]` **-创建标准辅助区域。</li><li>**/stub `<masterIPaddress>[,<masterIPaddress>...]` /File `<filename>` ** -创建支持文件的存根区域。</li><li>**/dsstub `<masterIPaddress>[,<masterIPaddress>...]` **-创建 active directory 集成存根区域。</li><li>**/forwarder `<masterIPaddress[,<masterIPaddress>]` .../File `<filename>` ** -指定创建的区域将未解析的查询转发到另一台 DNS 服务器。</li><li>**/dsforwarder** -指定创建的 active directory 集成区域将未解析的查询转发到另一台 DNS 服务器。</li></ul> |
| /overwrite_mem | 从 AD DS 中的数据覆盖 DNS 数据。 |
| /overwrite_ds | 覆盖 AD DS 中的现有数据。 |

##### <a name="remarks"></a>备注

- 如果将区域类型设置为 **/dsforwarder** ，则将创建执行条件性转发的区域。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zoneresettype test.contoso.com /primary /file test.contoso.com.dns
dnscmd dnssvr1.contoso.com /zoneresettype second.contoso.com /secondary 10.0.0.2
```

## <a name="dnscmd-zoneresume-command"></a>dnscmd/zoneresume 命令

启动先前暂停的指定区域。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneresume <zonename>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要恢复的区域的名称。 |

##### <a name="remarks"></a>备注

- 可以使用此操作从 **/zonepause**操作重新启动。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zoneresume test.contoso.com
```

## <a name="dnscmd-zoneupdatefromds-command"></a>dnscmd/zoneupdatefromds 命令

从 AD DS 更新指定的 active directory 集成区域。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zoneupdatefromds <zonename>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要更新的区域的名称。 |

##### <a name="remarks"></a>备注

- 默认情况下，Active directory 集成区域每五分钟执行一次此更新。 若要更改此参数，请使用 `dnscmd config dspollinginterval` 命令。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zoneupdatefromds
```

## <a name="dnscmd-zonewriteback-command"></a>dnscmd/zonewriteback 命令

在 DNS 服务器内存中检查与指定区域相关的更改，并将其写入持久性存储。

### <a name="syntax"></a>语法

```
dnscmd [<servername>] /zonewriteback <zonename>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| `<servername>` | 指定要管理的 DNS 服务器，由 IP 地址、FQDN 或主机名表示。 如果省略此参数，则使用本地服务器。 |
| `<zonename>` | 指定要更新的区域的名称。 |

##### <a name="remarks"></a>备注

- 这是一个区域级别的操作。 你可以使用 **/writebackfiles**操作更新 DNS 服务器上的所有区域。

#### <a name="examples"></a>示例

```
dnscmd dnssvr1.contoso.com /zonewriteback test.contoso.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
