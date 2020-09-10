---
title: 子命令集-服务器
description: 子命令集-服务器的参考文章，其中配置了 Windows 部署服务服务器的设置。
ms.topic: reference
ms.assetid: da55c29d-a94a-4d73-877b-af480f906ca0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 33ebdc4e411c7ff550b9686459e7440007d2ae63
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635472"
---
# <a name="subcommand-set-server"></a>子命令：设置-服务器

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

配置 Windows 部署服务服务器的设置。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Set-Server [/Server:<Server name>]
    [/Authorize:{Yes | No}]
    [/RogueDetection:{Yes | No}]
    [/AnswerClients:{All | Known | None}]
    [/Responsedelay:<time in seconds>]
    [/AllowN12forNewClients:{Yes | No}]
    [/ArchitectureDiscovery:{Yes | No}]
    [/resetBootProgram:{Yes | No}]
    [/DefaultX86X64Imagetype:{x86 | x64 | Both}]
    [/UseDhcpPorts:{Yes | No}]
    [/DhcpOption60:{Yes | No}]
    [/RpcPort:<Port number>]
    [/PxepromptPolicy
        [/Known:{OptIn | Noprompt | OptOut}]
        [/New:{OptIn | Noprompt | OptOut}]
    [/BootProgram:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/N12BootProgram:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/BootImage:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/PreferredDC:<DC Name>]
    [/PreferredGC:<GC Name>]
    [/PrestageUsingMAC:{Yes | No}]
    [/NewMachineNamingPolicy:<Policy>]
    [/NewMachineOU]
         [/type:{Serverdomain | Userdomain | UserOU | Custom}]
         [/OU:<Domain name of OU>]
    [/DomainSearchOrder:{GCOnly | DCFirst}]
    [/NewMachineDomainJoin:{Yes | No}]
    [/OSCMenuName:<Name>]
    [/WdsClientLogging]
         [/Enabled:{Yes | No}]
         [/LoggingLevel:{None | Errors | Warnings | Info}]
    [/WdsUnattend]
         [/Policy:{Enabled | Disabled}]
         [/CommandlinePrecedence:{Yes | No}]
         [/File:<path>]
             /Architecture:{x86 | ia64 | x64}
    [/AutoaddPolicy]
         [/Policy:{AdminApproval | Disabled}]
         [/PollInterval:{time in seconds}]
         [/MaxRetry:{Retries}]
         [/Message:<Message>]
         [/RetentionPeriod]
             [/Approved:<time in days>]
             [/Others:<time in days>]
    [/AutoaddSettings]
         /Architecture:{x86 | ia64 | x64}
         [/BootProgram:<Relative path>]
         [/ReferralServer:<Server name>
         [/WdsClientUnattend:<Relative path>]
         [/BootImage:<Relative path>]
         [/User:<Owner>]
         [/JoinRights:{JoinOnly | Full}]
         [/JoinDomain:{Yes | No}]
    [/BindPolicy]
         [/Policy:{Include | Exclude}]
         [/add]
              /address:<IP or MAC address>
              /addresstype:{IP | MAC}
         [/remove]
              /address:<IP or MAC address>
              /addresstype:{IP | MAC}
    [/RefreshPeriod:<time in seconds>]
    [/BannedGuidPolicy]
         [/add]
              /Guid:<GUID>
         [/remove]
             /Guid:<GUID>
    [/BcdRefreshPolicy]
         [/Enabled:{Yes | No}]
         [/RefreshPeriod:<time in minutes>]
    [/Transport]
         [/ObtainIpv4From:{Dhcp | Range}]
             [/start:<start IP address>]
             [/End:<End IP address>]
         [/ObtainIpv6From:Range]
             [/start:<start IP address>]
             [/End:<End IP address>]
         [/startPort:<start Port>
             [/EndPort:<start Port>
        [/Profile:{10Mbps | 100Mbps | 1Gbps | Custom}]
        [/MulticastSessionPolicy]
             [/Policy:{None | AutoDisconnect | Multistream}]
                 [/Threshold:<Speed in KBps>]
                 [/StreamCount:{2 | 3}]
                 [/Fallback:{Yes | No}]
        [/forceNative]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
|[/Authorize： {Yes &#124; No}]|指定是否在动态主机控制协议中授权此服务器 (DHCP) 。|
|[/RogueDetection： {Yes &#124; No}]|启用或禁用 DHCP rogue 检测。|
|[/AnswerClients： {All &#124; 已知 &#124; 无}]|指定此服务器将应答的客户端。 如果将此值设置为 " **已知**"，则必须在 Active Directory 域服务中预留一台计算机 (AD DS) ，然后 Windows 部署服务服务器将对该计算机进行应答。|
|[/Responsedelay： <time in seconds> ]|服务器在应答启动客户端之前将等待的时间。 此设置不适用于预留计算机。|
|[/AllowN12forNewClients： {Yes &#124; No}]|对于 Windows Server 2008，指定未知客户端无需按 F12 键即可启动网络启动。 已知客户端将收到为计算机指定的启动程序，如果未指定，则为体系结构指定的启动程序。<p>对于 Windows Server 2008 R2，此选项已替换为以下命令： wdsutil/Set-Server/PxepromptPolicy/New： Noprompt|
|[/ArchitectureDiscovery： {Yes &#124; No}]|启用或禁用体系结构发现。 这使得基于 x64 的客户端的发现无法正确地广播其体系结构。|
|[/resetBootProgram： {Yes &#124; No}]|确定是否将为刚启动的客户端擦除引导路径，而无需按 F12 键。|
|[/DefaultX86X64Imagetype： {x86 &#124; x64 &#124; 均为}]|控制将向基于 x64 的客户端显示的启动映像。|
|[/UseDhcpPorts： {Yes &#124; No}]|指定 PXE 服务器是否应尝试绑定到 DHCP 端口（TCP 端口67）。 如果 DHCP 和 Windows 部署服务在同一台计算机上运行，则应将此选项设置为 " **否** "，以便 dhcp 服务器使用该端口，并将 **/DhcpOption60** 参数设置为 **"是"**。 此值的默认设置为 **"是"**。|
|[/DhcpOption60： {Yes &#124; No}]|指定是否应为 PXE 支持配置 DHCP 选项60。 如果 DHCP 和 Windows 部署服务在同一服务器上运行，请将此选项设置为 **"是"** ，并将 **/UseDhcpPorts** 选项设置为 " **否**"。 此值的默认设置为 " **否**"。|
|[/RpcPort： <Port number> ]|指定用于为客户端请求服务的 TCP 端口号。|
|[/PxepromptPolicy]|配置已知 (预留) 和新客户端启动 PXE 启动的方式。 此选项仅适用于 Windows Server 2008 R2。 使用以下选项设置设置：<p>-[/Known： {OptIn&#124;选择&#124;Noprompt}]-设置预安排客户端的策略。<br />-[/New： {OptIn&#124;选择&#124;Noprompt}]-设置新客户端的策略。<p>**OptIn** 表示客户端需要按某个密钥才能进行 PXE 启动，否则它将回退到下一个启动设备。<p>**Noprompt** 表示客户端将始终 PXE 启动。<p>**选择** 表示客户端将 PXE 启动，除非按下 Esc 键。|
|[/BootProgram： <Relative path> ]/Architecture： {x86 &#124; ia64 &#124; x64}|指定 remoteInstall 文件夹中启动程序的相对路径 (例如 **boot\x86\pxeboot.n12**) ，并指定启动程序的体系结构。|
|[/N12BootProgram： <Relative path> ]/Architecture： {x86 &#124; ia64 &#124; x64}|指定引导程序的相对路径，该路径不要求按 F12 键 (例如 **boot\x86\pxeboot.n12**) ，并指定启动程序的体系结构。|
|[/BootImage： <Relative path> ]/Architecture： {x86 &#124; ia64 &#124; x64}|指定启动客户端应接收的启动映像的相对路径，并指定启动映像的体系结构。 可以为每个体系结构指定此项。|
|[/PreferredDC： <DC Name> ]|指定 Windows 部署服务应使用的域控制器的名称。 此名称可以是 NetBIOS 名称或 FQDN。|
|[/PreferredGC： <GC Name> ]|指定 Windows 部署服务应使用的全局编录服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。|
|[/PrestageUsingMAC： {Yes &#124; No}]|指定在 AD DS 中创建计算机帐户时 Windows 部署服务是否应使用 MAC 地址而不是 GUID/UUID 来识别计算机。|
|[/NewMachineNamingPolicy： <Policy> ]|指定为客户端生成计算机名时要使用的格式。 有关要用于的格式的信息 <policy> ，请在 mmc 管理单元中右键单击该服务器，单击 "  **属性**"，并查看 " **目录服务** " 选项卡。例如， **/NewMachineNamingPolicy：% 61Username% #**。|
|[/NewMachineOU]|用于指定将在其中创建客户端计算机帐户 AD DS 中的位置。 使用以下选项指定位置。<p>-[/type： Serverdomain &#124; Userdomain &#124; UserOU &#124; 自定义] 指定位置的类型。 **Serverdomain** 在与 Windows 部署服务服务器相同的域中创建帐户。 **Userdomain** 在执行安装的用户所在的域中创建帐户。 **UserOU** 在执行安装的用户的组织单位中创建帐户。 **自定义** 允许你指定自定义位置 (你还必须使用此选项指定 **/ou** 的值) 。<br />-[/OU： <Domain name of OU> ]-如果为 **/type**选项指定**Custom** ，此选项将指定应在其中创建计算机帐户的组织单位。|
|[/DomainSearchOrder： {GCOnly &#124; DCFirst}]|指定 AD DS (全局编录或域控制器) 中搜索计算机帐户的策略。|
|[/NewMachineDomainJoin： {Yes &#124; No}]|指定在安装过程中是否应将尚未预留 AD DS 的计算机加入域。 默认设置为“是”。|
|/WdsClientLogging|指定服务器的日志记录级别。<p>-[/Enabled： {Yes &#124; No}]-启用或禁用 Windows 部署服务客户端操作的日志记录。<br />-[/LoggingLevel： {None &#124; 错误 &#124; 警告 &#124; 信息}-设置日志记录级别。 "**无**" 等效于禁用日志记录。 **错误** 是日志记录的最低级别，表示只记录错误。 **警告** 同时包含警告和错误。 **Info** 是日志记录的最高级别，包括错误、警告和信息性事件。|
|/WdsUnattend|这些设置控制 Windows 部署服务客户端的无人参与安装行为。 使用以下选项设置设置：<p>-[/Policy： {Enabled &#124; Disabled}]-指定是否使用无人参与安装。<br />-[/CommandlinePrecedence： {Yes &#124; No}]-指定在客户端安装过程中，如果在客户) 端上存在 Autounattend.xml 文件 (（如果在客户端安装过程中使用/Unattend 选项直接传递给 Windows 部署服务客户端）或无人参与的安装程序文件，则为。 默认设置为 " **否**"。<br />-[/File： <Relative path> /Architecture： {x86 &#124; ia64 &#124; x64}]-指定无人参与文件的文件名、路径和体系结构。|
|[/AutoaddPolicy]|这些设置控制自动添加策略。 您可以使用以下选项定义这些设置：<p>-[/Policy： {AdminApproval &#124; Disabled}]- **AdminApprove** 导致将所有未知计算机添加到挂起的队列中，然后，管理员可以根据需要查看计算机列表并批准或拒绝每个请求。 **Disabled** 表示当未知计算机尝试启动到服务器时，不会执行任何其他操作。<br />-[/PollInterval： {time in seconds}]-指定网络启动程序应轮询 Windows 部署服务服务器的时间间隔 (秒) 。<br />-[/MaxRetry： <Number> ]-指定网络启动程序轮询 Windows 部署服务服务器的次数。 此值与 **/PollInterval**一起决定了网络启动程序在超时前等待管理员批准或拒绝计算机的时间。例如， **MaxRetry** 值为10， **PollInterval** vlue 为60，表示客户端应轮询服务器10次，并在两次尝试之间等待60秒。 因此，客户端会在10分钟后超时 (10 x 60 秒 = 10 分钟) 。<br />-[/Message： <Message> ]-指定在网络启动程序对话框页面上向客户端显示的消息。<br />-[/RetentionPeriod]-指定计算机在被自动清除之前可处于挂起状态的天数。<br />-[/Approved： <time in days> ]-指定批准的计算机的保持期。 必须将此参数与 **/RetentionPeriod** 选项一起使用。<br />-[/Others： <time in days> ]-指定拒绝或挂起)  (未批准的计算机的保持期。 必须将此参数与 **/RetentionPeriod** 选项一起使用。|
|[/AutoaddSettings]|指定要应用于每台计算机的默认设置。 您可以使用以下选项定义这些设置：<p>-/Architecture： {x86 &#124; ia64 &#124; x64}-指定体系结构。<br />-[/BootProgram： <Relative path> ]-指定发送到已批准计算机的启动程序。 如果未指定启动程序，则将使用服务器) 上指定的计算机 (体系结构的默认值。<br />-[/WdsClientUnattend： <Relative path> ]-设置经过批准的客户端应接收的无人参与文件的相对路径。<br />-[/ReferralServer： <Server name> ]-指定客户端将用于下载映像的 Windows 部署服务服务器。<br />-[/BootImage： <Relative path> ]-指定已批准的客户端将接收的启动映像。<br />-[/User： <Domain\User &#124; User@Domain>]-在计算机帐户对象上设置权限，为指定的用户指定将计算机加入域所需的权限。<br />-[JoinRights： {JoinOnly &#124; Full}]-指定要分配给用户的权限类型。 **JoinOnly** 要求管理员重置计算机帐户，然后用户才能将计算机加入域。 **Full** 给予用户完全访问权限，包括将计算机加入域的权限。<br />-[/JoinDomain： {Yes &#124; No}]-指定在 Windows 部署服务安装过程中是否应将计算机作为此计算机帐户加入到域。 默认设置为“是”。|
|/BindPolicy|配置 PXE 提供程序要侦听的网络接口。 使用以下选项定义策略：<p>-[/Policy： {Include &#124; Exclude}]-设置接口绑定策略，以包含或排除接口列表上的地址。<br />-[/add]-向列表添加接口。 还必须指定/addresstype 和/address。<br />-[/remove]-从列表中删除接口。 还必须指定/addresstype 和/address。<br />-/address： <IP or MAC address> -指定要添加或删除的接口的 IP 或 MAC 地址。<br />-/addresstype： {IP &#124; MAC}-指示 **/address** 选项中指定的地址类型。|
|[/RefreshPeriod： <seconds> ]|指定服务器刷新其设置)  (的频率（以秒为单位）。|
|[/BannedGuidPolicy]|使用以下选项管理禁止 Guid 列表：<p>-[/add]/Guid： <GUID> -将指定的 Guid 添加到禁止 guid 的列表。 此 GUID 的任何客户端都将被其 MAC 地址标识。<br />-[/remove]/Guid： <GUID> -从禁止 guid 列表中删除指定的 Guid。|
|/BcdRefreshPolicy|使用以下选项配置用于刷新 Bcd 文件的设置：<p>-[/Enabled： {Yes &#124; No}]-指定 Bcd 刷新策略。 如果 **/Enabled** 设置为 **"是"**，则会在指定的时间间隔内刷新 Bcd 文件。<br />-[/RefreshPeriod： <time in minutes> ]-指定刷新 Bcd 文件的时间间隔。|
|/传输|配置以下选项：<p><ul><li>[/ObtainIpv4From： {Dhcp &#124; 范围}]-指定 IPv4 地址的源。<p><ul><li>[/start： <starting Ipv4 address> ]-指定 IP 地址范围的起始地址。 仅当 **/ObtainIpv4From**设置为**Range**时，此选项才是必需的并且有效。</li><li>[/End： <Ending Ipv4 address> ]-指定 IP 地址范围的结束。 仅当 **/ObtainIpv4From** 设置为 **Range**时，此选项才是必需的并且有效。</li></ul></li><li>[/ObtainIpv6From： Range][/start： <start IP address> ][/End： <End IP address> ] 指定 IPv6 地址的源。 此选项仅适用于 Windows Server 2008 R2，唯一受支持的值为范围。</li><li>[/startPort： <starting port> ]-指定端口范围的开头。</li><li>[/EndPort： <Ending port> ]-指定端口范围的结尾。</li><li>[/Profile： {10Mbps &#124; 100Mbps &#124; 1Gbps &#124; Custom}]-指定要使用的网络配置文件。 只有运行 Windows Server 2008 的 forservers 才支持此选项。</li><li>[/MulticastSessionPolicy] 配置多播传输的传输设置。 此命令仅适用于 Windows Server 2008 R2。<p><ul><li>[/Policy： {None &#124; AutoDisconnect &#124; Multistream}]-确定如何处理速度缓慢的客户端。 "无" 表示将所有客户端保持在一个会话中的速度相同。 AutoDisconnect 表示将断开到指定/Threshold 下的任何客户端的连接。 Multistream 表示客户端将被划分为/StreamCount. 指定的多个会话。</li><li>[/Threshold： <Speed in KBps> ]-对于/Policy： AutoDisconnect，此选项设置以 KBps 为单位的最小传输速率。 低于此速率的客户端将与多播传输断开连接。</li><li>[/StreamCount： {2 &#124; 3}][/Fallback： {Yes &#124; No}]-对于/Policy： Multistream，此选项确定会话数。 2表示两个会话 (速度快且速度缓慢) 3 表示三个会话 (慢、中、快速) 。</li><li>[/Fallback： {Yes&#124; No}]-确定断开连接的客户端是否将使用另一种方法继续传输 (如果客户端) 支持此方法。 如果你使用的是 WDS 客户端，则计算机将回退为单播。 Wdsmcast.exe 不支持回退机制。 此选项也适用于不支持 Multistream 的客户端。 在这种情况下，计算机将回退到其他方法，而不是移到较慢的传输会话。</li></ul></li></ul>|
## <a name="examples"></a>示例
若要将服务器设置为仅应答已知的客户端，响应延迟为4分钟，请键入：
```
wdsutil /Set-Server /AnswerClients:Known /Responsedelay:4
```
若要设置服务器的启动程序和体系结构，请键入：
```
wdsutil /Set-Server /BootProgram:boot\x86\pxeboot.n12 /Architecture:x86
```
若要在服务器上启用日志记录，请键入：
```
wdsutil /Set-Server /WdsClientLogging /Enabled:Yes /LoggingLevel:Warnings
```
若要在服务器上启用无人参与，以及体系结构和客户端无人参与文件，请键入：
```
wdsutil /Set-Server /WdsUnattend /Policy:Enabled /File:WDSClientUnattend \unattend.xml /Architecture:x86
```
若要将预启动执行环境 (PXE) 服务器设置为尝试绑定到 TCP 端口67和60，请键入：
```
wdsutil /Set-server /UseDhcpPorts:No /DhcpOption60:Yes
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 disable-Server 命令](using-the-disable-server-command.md) 
[使用 enable-Server 命令](using-the-enable-server-command.md) 
[使用 get-Server 命令](using-the-get-server-command.md) 
[使用 Initialize-Server 命令](using-the-initialize-server-command.md) 
[子命令：启动-服务器](subcommand-start-server.md) 
[子命令：停止-服务器](subcommand-stop-server.md) 
["取消初始化服务器" 选项](the-uninitialize-server-option.md)
