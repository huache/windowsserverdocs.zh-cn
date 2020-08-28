---
title: nfsadmin
description: 用于管理 NFS 服务器和 NFS 客户端的 nfsadmin 命令的参考文章。
ms.topic: reference
ms.assetid: 7375b2cf-c6b8-45b5-abf6-6c10e462defd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e7329b26b201bd99a71bb30f50e9f5ba95953846
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023641"
---
# <a name="nfsadmin"></a>nfsadmin

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

一种命令行实用工具，用于在运行 Microsoft Services for 网络文件系统 (NFS) 的本地或远程计算机上管理 NFS 服务器或客户端 NFS 服务器。 使用不带参数的 nfsadmin 服务器将显示当前的 NFS 服务器配置设置，nfsadmin 客户端将显示当前的 NFS 客户端配置设置。

## <a name="syntax"></a>语法

```
nfsadmin server [computername] [-u Username [-p Password]] -l
nfsadmin server [computername] [-u Username [-p Password]] -r {client | all}
nfsadmin server [computername] [-u Username [-p Password]] {start | stop}
nfsadmin server [computername] [-u Username [-p Password]] config option[...]
nfsadmin server [computername] [-u Username [-p Password]] creategroup <name>
nfsadmin server [computername] [-u Username [-p Password]] listgroups
nfsadmin server [computername] [-u Username [-p Password]] deletegroup <name>
nfsadmin server [computername] [-u Username [-p Password]] renamegroup <oldname> <newname>
nfsadmin server [computername] [-u Username [-p Password]] addmembers <hostname>[...]
nfsadmin server [computername] [-u Username [-p Password]] listmembers
nfsadmin server [computername] [-u Username [-p Password]] deletemembers <hostname><groupname>[...]
nfsadmin client [computername] [-u Username [-p Password]] {start | stop}
nfsadmin client [computername] [-u Username [-p Password]] config option[...]
```

### <a name="general-parameters"></a>常规参数

| 参数 | 说明 |
| --------- | ----------- |
| computername | 指定要管理的远程计算机。 你可以使用 Windows Internet 名称服务指定计算机 (WINS) 名称或域名系统 (DNS) 名称或 Internet 协议 (IP) 地址。 |
| -u 用户名 | 指定要使用其凭据的用户的用户名。 可能需要以 "域 *\ 用户名*" 格式将域名添加到用户名。 |
| -p 密码 | 指定使用 **-u** 选项指定的用户的密码。 如果指定 **-u** 选项，但忽略 **-p** 选项，则系统会提示输入用户的密码。 |

### <a name="server-for-nfs-related-parameters"></a>NFS 服务器相关参数

| 参数 | 说明 |
| --------- | ----------- |
| -l | 列出客户端持有的所有锁。 |
| -r `{client|all}` | 释放由客户端持有的锁，如果所有客户端均指定了 all，则为。 |
| start | 启动 NFS 服务器服务。 |
| stop | 停止 NFS 服务器服务。 |
| config | 指定 NFS 服务器的常规设置。 必须至少提供以下选项之一和 **config** 命令参数：<ul><li>**mapsvr = `<server>` **-将服务器设置为 NFS 服务器的用户名映射服务器。 尽管此选项仍可与以前版本的兼容性一起使用，但你应改为使用 sfuadmin 实用程序。</li><li>**auditlocation = `{eventlog|file|both|none}` **-指定是否审核事件以及记录事件的位置。 需要以下参数之一：<ul><li>**eventlog** -指定将仅在事件查看器应用程序日志中记录审核的事件。</li><li>**文件** -指定将仅在指定的文件中记录已审核的事件 `config fname` 。</li><li>**两者** -指定审核事件将记录在事件查看器应用程序日志以及由指定的文件中 `config fname` 。</li><li>**无** -指定不审核事件。</li></ul><li>**fname = `<file>` **-将文件指定的文件设置为审核文件。 默认值为 **%sfudir%\log \\ nfssvr**。</li><li>**fsize = `<size>` **-将大小设置为审核文件的最大大小（mb）。 默认的最大大小为 **7 MB**。</li><li>**`audit=[+|-]mount [+|-]read [+|-]write [+|-]create [+|-]delete [+|-]locking [+|-]all`** -指定要记录的事件。 若要开始记录事件，请在事件名称之前键入一个加号 (**+**) ; 若要停止记录事件，请在 **-** 事件名称之前键入减号 () 。 如果省略符号，则假定为 **+** 符号。 不要将 **所有** 事件与任何其他事件名称一起使用。</li><li>**lockperiod = `<seconds>` **-指定在到 NFS 服务器的连接丢失然后重新建立，或在 NFS 服务器服务重新启动后，NFS 服务器等待回收锁的秒数。</li><li>**portmapprotocol = `{TCP|UDP|TCP+UDP}` **-指定 Portmap 支持的传输协议。 默认设置为 **TCP + UDP**。</li><li>**mountprotocol = `{TCP|UDP|TCP+UDP}` **-指定装载支持的传输协议。 默认设置为 **TCP + UDP**。</li><li>**nfsprotocol = `{TCP|UDP|TCP+UDP}` **-指定网络文件系统 (NFS) 支持的传输协议。 默认设置为 **TCP + UDP**</li><li>**nlmprotocol = `{TCP|UDP|TCP+UDP}` **-指定网络锁定管理器 (NLM) 支持哪种传输协议。 默认设置为 **TCP + UDP**。</li><li>**nsmprotocol = `{TCP|UDP|TCP+UDP}` **-指定网络状态管理器 (NSM) 支持的传输协议。 默认设置为 **TCP + UDP**。</li><li>**enableV3 = `{yes|no}` **-指定是否将支持 NFS 版本3协议。 默认设置为 **"是"**。</li><li>**renewauth = `{yes|no}` **-指定在 config renewauthinterval 指定的时间段后是否需要重新进行身份验证的客户端连接。 默认设置为 " **否**"。</li><li>**renewauthinterval = `<seconds>` **-如果 `config renewauth` 设置为 **"是"**，则指定在强制重新进行身份验证之前经过的秒数。 默认值为 **600 秒**。</li><li>**dircache = `<size>` **-指定目录缓存的大小（kb）。 指定为 size 的数字必须是4到128之间的4的倍数。 默认目录缓存大小为 **128 KB**。</li><li>**translationfile = `<file>` **-指定一个文件，该文件包含用于在从基于 Windows 的到基于 UNIX 的文件系统移动文件时替换文件名称中的字符的映射信息。 如果未指定文件，则将禁用文件名字符转换。 如果 **translationfile** 的值已更改，则必须重新启动服务器才能使更改生效。</li><li>**dotfileshidden = `{yes|no}` **-指定名称以句点开头的文件是否 (。 ) 在 Windows 文件系统中标记为隐藏，因而对 NFS 客户端隐藏。 默认设置为 " **否**"。</li><li>**casesensitivelookups = `{yes|no}` **-指定目录查找是否区分大小写 (需要完全匹配字符大小写) 。<p>还必须禁用 Windows 内核不区分大小写，以支持区分大小写的文件名。 若要支持区分大小写，请将注册表项的 **DWord** 值更改 `HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\kernel` 为 **0**。</li><li>**ntfscase = `{lower|upper|preserve}` **-指定 NTFS 文件系统中文件名称的大小写是否以小写、大写或存储在目录中的形式返回。 默认设置为 " **保留**"。 如果 **casesensitivelookups** 设置为 **"是"**，则无法更改此设置。</li></ul> |
| creategroup `<name>` | 创建新的客户端组，并为其指定名称。 |
| listgroups | 显示所有客户端组的名称。 |
| deletegroup `<name>` | 删除由名称指定的客户端组。 |
| renamegroup `<oldname>``<newname>` | 将 *oldname* 指定的客户端组的名称更改为 *newname*。 |
| addmembers `<hostname>[...]` | 将 *主机* 添加到按 *名称*指定的客户端组。 |
| listmembers `<name>` | 列出由 *名称*指定的客户端组中的主机。 |
| deletemembers `<hostname><groupname>[...]` | 从*组*指定的客户端组中删除*主机*指定的客户端。 |

### <a name="client-for-nfs-related-parameters"></a>NFS 客户端相关参数

| 参数 | 说明 |
| --------- | ----------- |
| start | 启动 NFS 客户端服务。 |
| stop | 停止 NFS 客户端服务。 |
| config | 指定 NFS 客户端的常规设置。 必须至少提供以下选项之一和 **config** 命令参数：<ul><li>**fileaccess = `<mode>` **-指定在网络文件系统 (NFS) 服务器上创建的文件的默认权限模式。 **Mode**参数由三位数字组成，其中0到 7 (包含) ，表示授予用户、组和其他权限的默认权限。 这些数字转换为 UNIX 样式权限，如下所示： *0 = 无*; *1 = x (执行) *， *2 = w (只写入) *， *3 = wx (写入和执行) *， *4 = r (只读) *， *5 = rx * (读取和执行) ， *6 = rw * (读取和执行) ，6 = *rwx (读取、写入和执行) *。 例如，向 `fileaccess=750` 所有者授予 "读取"、"写入" 和 "执行" 权限，对组具有 "读取" 和 "执行" 权限，而对其他用户没有访问权限。</li><li>**mapsvr = `<server>` **-将服务器设置为适用于 NFS 的客户端的用户名映射服务器。 尽管此选项仍可与以前版本的兼容性一起使用，但你应改为使用 sfuadmin 实用程序。</li><li>**mtype = `{hard|soft}` **-指定默认装载类型。 对于硬装载，NFS 客户端会继续重试失败的 RPC，直到成功。 对于软装载，NFS 客户端在重试后将失败返回到调用应用程序。</li><li>**重试 `<number>` =**-指定尝试建立软装载连接的次数。 此值必须介于1到10（含）之间。 默认值为 **1**。</li><li>**超时 = `<seconds>` **-指定等待连接 (远程过程调用) 的秒数。 此值必须是 *0.8*、 *0.9*或从 *1 到 60*的整数（包括1和）。 默认值为 **0.8**。</li><li>**协议 = `{TCP|UDP|TCP+UDP}` **-指定客户端支持的传输协议。 默认设置为 **TCP + UDP**。</li><li>**rsize = `<size>` **-指定读取缓冲区的大小（以 kb 为单位）。 此值可以是 *0.5、1、2、4、8、16* 或 *32*。 默认值为 **32**。</li><li>**wsize = `<size>` **-指定写入缓冲区的大小（以 kb 为单位）。 此值可以是 *0.5、1、2、4、8、16* 或 *32*。 默认值为 **32**。</li><li>**perf = 默认** 值-将以下性能设置还原为默认值： *mtype*、 *retry*、 *timeout*、 *rsize*或 *wsize*。 |

### <a name="examples"></a>示例

要停止 NFS 服务器或 NFS 客户端，请键入：

```
nfsadmin server stop
nfsadmin client stop
```

若要启动 NFS 服务器或 NFS 客户端，请键入：

```
nfsadmin server start
nfsadmin client start
```

若要将 NFS 服务器设置为不区分大小写，请键入：

```
nfsadmin server config casesensitive=no
```

若要将 NFS 客户端设置为区分大小写，请键入：

```
nfsadmin client config casesensitive=yes
```

若要显示 "所有 NFS 服务器" 或 "NFS 客户端" 选项，请键入：

```
nfsadmin server config
nfsadmin client config
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [NFS cmdlet 参考](/powershell/module/nfs)
