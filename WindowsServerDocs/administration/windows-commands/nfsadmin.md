---
title: nfsadmin
description: '适用于 * * * * 的 Windows 命令主题 '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7375b2cf-c6b8-45b5-abf6-6c10e462defd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2658cf610e4328d382b9224f4230d68a022d1cc3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373230"
---
# <a name="nfsadmin"></a>nfsadmin

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

你可以使用**nfsadmin**来管理 nfs 服务器和 Nfs 客户端。  
  
## <a name="syntax"></a>语法  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` \-l  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` \-*r `{``|``}`*  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p*密码*`]] {`开始 `|` 停止`}`  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` config*选项*`[...]`  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` creategroup *Name*  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` listgroups  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` deletegroup *Name*  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` renamegroup *OldName NewName*  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` addmembers*名称主机*`[...]`  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` listmembers  
  
**nfsadmin server** `[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` deletemembers*组主机*`[...]`  
  
**nfsadmin 客户端**`[`*computerName*`] [`\-u*用户名*`[`\-p*密码*`]] {`开始 `|` 停止`}`  
  
**nfsadmin 客户端**`[`*computerName*`] [`\-u*用户名*`[`\-p *Password*`]]` config*选项*`[...]`  
  
## <a name="description"></a>描述  
**Nfsadmin**命令\-行实用程序在运行 Microsoft Services For 网络文件系统 \(nfs\)的本地或远程计算机上管理 nfs 服务器或客户端 nfs 服务器。 如果使用不具备所需权限的帐户登录，则可以指定帐户的用户名和密码。 **Nfsadmin**执行的操作取决于提供的命令参数。  
  
除了服务\-特定的命令参数和选项外， **nfsadmin**还接受以下内容：  
  
*computerName*  
指定要管理的远程计算机。 你可以使用 Windows Internet 名称服务指定计算机 \(WINS\) 名称或域名系统 \(DNS\) 名称或 Internet 协议 \(IP\) 地址。  
  
**\-u** *用户名*  
指定要使用其凭据的用户的用户名。 可能需要将域名添加到 "<em>域</em> **\\** <em>用户名</em>" 格式的用户名中  
  
**\-p** *密码*  
指定使用 **\-u**选项指定的用户的密码。 如果指定 **\-u**选项但省略 **\-p**选项，系统会提示用户输入密码。  
  
#### <a name="administering-server-for-nfs"></a>管理 NFS 服务器  
使用**nfsadmin 服务器**命令管理 NFS 服务器。 **Nfsadmin 服务器**采取的特定操作取决于指定的命令选项或参数：  
  
**\-l**  
列出客户端持有的所有锁。  
  
**\-r** {*client* | **all**}  
释放由*客户端*持有的锁，如果所有客户端均指定了**all** ，则为。  
  
**start**  
启动 NFS 服务器服务。  
  
**stop**  
停止 NFS 服务器服务。  
  
**config**  
指定 NFS 服务器的常规设置。 必须至少提供以下选项之一和**config**命令参数：  
  
**mapsvr\=** <em>服务器</em>  
将*服务器*设置为 NFS 服务器的用户名映射服务器。 尽管此选项仍可与以前版本的兼容性一起使用，但你应改为使用**sfuadmin**实用程序。  
  
**auditlocation\=** {**eventlog** | **文件** | **都** | **none**}  
指定是否审核事件以及记录事件的位置。 需要以下参数之一。  
  
**事件日志**  
指定仅在事件查看器应用程序日志中记录已审核的事件。  
  
**file**  
指定仅在由**config fname**指定的文件中记录已审核的事件。  
  
**全部**  
指定将在事件查看器应用程序日志以及**config fname**指定的文件中记录已审核的事件。  
  
**内容**  
指定将不审核事件。  
  
**fname\=** <em>文件</em>  
将*文件*指定的文件设置为审核文件。 默认值为% sfudir%\\日志\\nfssvr  
  
**fsize\=** \=*大小*  
将*size*设置为审核文件的最大大小（mb）。 默认的最大大小为 7 MB。  
  
**|\-\]\[** **\+|\-** **\]\[** **\+** **|\-** **\]** \[ **\+|** **\-** **\]\[\+** |\-\] **\+** \[ **\=** \[ **\+** | **\-** \] **\[\+|** **\-\]**  
指定要记录的事件。 若要开始记录事件，请在事件名称之前键入一个加号 \( **\+** \);若要停止记录事件，请在事件名称之前键入减号 \( **\-** \)。 如果省略符号，则采用加号。 不要将**所有**事件与任何其他事件名称一起使用。  
  
**lockperiod\=** <em>秒</em>  
指定在连接到 NFS 服务器的连接后，或在重启 nfs 服务器服务之后，NFS 服务器等待回收锁的秒数。  
  
Portmapprotocol\={TCP |UDP |TCP\+UDP  
指定 Portmap 支持的传输协议。 默认设置为**TCP\+UDP**。  
  
mountprotocol\={TCP |UDP |TCP\+UDP}  
指定装载支持的传输协议。 默认设置为**TCP\+UDP**。  
  
nfsprotocol\={TCP |UDP |TCP\+UDP}  
指定网络文件系统 \(NFS\) 支持的传输协议。 默认设置为**TCP\+UDP**  
  
nlmprotocol\={TCP |UDP |TCP\+UDP}  
指定 \(NLM\) 支持哪种传输协议。 默认设置为**TCP\+UDP**。  
  
nsmprotocol\={TCP |UDP |TCP\+UDP}  
指定网络状态管理器 \(NSM\) 支持的传输协议。 默认设置为**TCP\+UDP**。  
  
**enableV3\=** {**yes** | **no**}  
指定是否将支持 NFS 版本3协议。 默认设置为 **"是"** 。  
  
**renewauth\=** {**yes** | **no**}  
指定在**config renewauthinterval**指定的时间段后，是否需要重新进行身份验证客户端连接。 默认设置为 "**否**"。  
  
**renewauthinterval\=** <em>秒</em>  
指定在**配置 renewauth**设置为 **"是"** 时，强制重新进行身份验证的客户端之前经过的秒数。 默认值为600秒。  
  
**dircache\=** <em>大小</em>  
指定目录缓存的大小（kb）。 指定为*size*的数字必须是4到128之间的4的倍数。 默认目录\-缓存大小为 128 KB。  
  
**translationfile**\=\[文件\]  
指定一个文件，该文件包含用于在基于 UNIX\-文件系统从 Windows\-移动时替换文件名称中的字符的映射信息。 如果未指定*文件*，则将禁用文件名字符转换。 如果**translationfile**的值已更改，则必须重新启动服务器才能使更改生效。  
  
**dotfileshidden**\={**yes** | **no**}  
指定创建的文件的名称是否以句点开头 \(。\) 将在 Windows 文件系统中标记为隐藏，因而会在 NFS 客户端中隐藏。 默认设置为 "**否**"。  
  
**casesensitivelookups\=** {**yes** | **no**}  
指定目录查找是否区分大小写 \(是否需要完全匹配字符大小写\)。  
  
还需要禁用\-不区分的 Windows 内核案例，以便 NFS 服务器支持\-敏感文件名称的大小写。 可以通过将以下注册表项清除为0来禁用 Windows 内核 case\-不区分大小写：  
  
HKLM\\SYSTEM\\CurrentControlSet\\控件\\会话管理器\\内核  
  
DWOrd obcaseinsensitive   
  
> [!IMPORTANT]  
> 本部分仅适用于 Windows Server 2008 R2、Windows Server 2008 和 Windows Server 2003。 本部分不适用于 Windows Server 2012 R2 或 Windows Server 2012。  
  
**ntfscase\=** { ** | ** **上** | **保留**}  
指定 NTFS 文件系统中文件名称的大小写是否以小写、大写或存储在目录中的形式返回。 默认设置为 "**保留**"。 如果**casesensitivelookups**设置为 **"是"** ，则无法更改此设置。  
  
**creategroup** *名称*  
创建新的客户端组，并为其指定*名称*。  
  
**listgroups**  
显示所有客户端组的名称。  
  
**deletegroup** *名称*  
删除由*名称*指定的客户端组。  
  
**renamegroup** *OldName NewName*  
将*OldName*指定的客户端组的名称更改为*NewName*  
  
**addmembers** *Name Host*\[...\]  
将*主机*添加到按*名称*指定的客户端组。  
  
**listmembers** *名称*  
列出由*名称*指定的客户端组中的主机。  
  
**deletemembers** *组主机*\[...\]  
从*组*指定的客户端组中删除*主机*指定的客户端。  
  
如果未指定命令选项或参数，则**nfsadmin 服务器**将显示 NFS 的当前服务器配置设置。  
  
#### <a name="administering-client-for-nfs"></a>管理 NFS 客户端  
使用**nfsadmin 客户端**命令管理 NFS 客户端。 **Nfsadmin 客户端**所采用的具体操作取决于指定的命令参数：  
  
**start**  
启动 NFS 客户端服务。  
  
**stop**  
停止 NFS 客户端服务。  
  
**config**  
指定 NFS 客户端的常规设置。 必须至少提供以下选项之一和**config**命令参数：  
  
**fileaccess\=** <em>模式</em>  
-   指定在网络文件系统 \(NFS\) 服务器上创建的文件的默认权限模式。 *Mode*参数由0到 7 \(包含的三位数组成\) 表示授予用户、组和其他 \(分别\)的默认权限。 数字转换为 UNIX\-样式权限，如下所示： 0\=无，1\=x，2\=w，3\=wx，4\=r，5\=rx，6\=rw，7\=rwx。 例如， **fileaccess\=750**向所有者授予 rwx 权限，对组具有 rx 权限，对其他用户不具有访问权限。  
  
**mapsvr\=** <em>服务器</em>  
将*服务器*设置为 NFS 客户端的用户名映射服务器。 尽管此选项仍可与以前版本的兼容性一起使用，但你应改为使用**sfuadmin**实用程序。  
  
**mtype\=** {**hard** | **软**}  
指定默认装载类型。 对于硬装载，NFS 客户端会继续重试失败的 RPC，直到成功。 对于软装载，NFS 客户端在**重试后**将失败返回到调用应用程序。  
  
**重试\=** <em>号</em>  
指定尝试建立软装载连接的次数。 此值必须介于1到10（含）之间。 默认值为 1。  
  
**超时\=** <em>秒</em>  
指定 \(远程过程调用\)的连接的等待时间（以秒为单位）。 此值必须是0.8、0.9 或从1到60的整数（包括1和）。 默认值为0.8。  
  
**协议\={TCP |UDP |TCP\+UDP}**  
指定客户端支持的传输协议。 默认设置为**TCP\+UDP**  
  
**rsize\=** <em>大小</em>  
指定读取缓冲区的大小（以 kb 为单位）。 此值可以是0.5、1、2、4、8、16或32。 默认值为32。  
  
**wsize\=** <em>大小</em>  
指定写入缓冲区的大小（以 kb 为单位）。 此值可以是0.5、1、2、4、8、16或32。 默认值为32。  
  
**perf\=默认值**  
将以下性能设置还原为默认值：  
  
-   **mtype**  
  
-   **后**  
  
-   **timeout**  
  
-   **rsize**  
  
-   **wsize**  
  
**fileaccess\=** <em>模式</em>  
指定在网络文件系统 \(NFS\) 服务器上创建的文件的默认权限模式。 *Mode*参数由0到 7 \(包含的三位数组成\) 表示授予用户、组和其他 \(分别\)的默认权限。 数字转换为 UNIX\-样式权限，如下所示： 0\=无，1\=x，2\=w，3\=wx，4\=r，5\=rx，6\=rw，7\=rwx。 例如， **fileaccess\=750**向所有者授予 rwx 权限，对组具有 rx 权限，对其他用户不具有访问权限。  
  
如果未指定命令选项或参数，则**nfsadmin 客户端**将显示当前的 NFS 客户端配置设置。  
  

