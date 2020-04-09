---
title: 批准-AutoaddDevices
description: 适用于 AutoaddDevices 的 Windows 命令主题，用于审批等待管理审批的计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8d76e8d3-ab35-429c-be7b-904f95d0782d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b7f63faabf37337136cad186fd252915adf1a743
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831830"
---
# <a name="approve-autoadddevices"></a>批准-AutoaddDevices

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

批准等待管理审批的计算机。 启用自动添加策略后，在未知计算机（未预留的计算机）之前需要管理审批才能安装映像。 你可以使用 "服务器 s 属性" 页的 " **PXE 响应**" 选项卡启用此策略。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Approve-AutoaddDevices [/Server:<Server name>] /RequestId:{<Request ID>| ALL} [/MachineName:<Device name>] [/OU:<DN of OU>] 
[/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>] [/BootImagepath:<Relative path>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
|/RequestId： {Request ID &#124; ALL}|指定分配给挂起计算机的请求 ID。 指定 "**全部**" 以批准所有挂起的计算机。|
|[/MachineName：<Device name>]|指定要添加的计算机的名称。 在批准所有计算机时，不能使用此选项。|
|[/OU：<DN of OU>]|指定应在其中创建计算机帐户对象的组织单位（OU）的可分辨名称。 例如： **OU = MyOU，CN = Test，dc = Domain，DC = com**。 默认位置是默认计算机的容器。|
|[/User： < Domain\User &#124; User@Domain>]|在计算机帐户对象上设置权限，以便为指定的用户分配所需的权限。|
|[/JoinRights： {JoinOnly &#124; Full}]|指定要分配给指定用户的权限类型。<p>-   **JoinOnly**要求管理员重置计算机帐户，然后用户才能将计算机加入域。<br />-   **full**为用户提供完全访问权限，包括将计算机加入域的权限。|
|[/JoinDomain： {Yes &#124; No}]|指定是否应在操作系统安装过程中将计算机加入域作为此计算机帐户。 默认值为 **"是"** 。|
|[/ReferralServer：<Server name>]|指定要连接的服务器的名称，以使用普通文件传输协议（tftp）下载网络启动程序和启动映像。|
|[/BootProgram：<Relative path>]|指定从 remoteInstall 文件夹到此计算机应接收的网络引导程序的相对路径。 例如： **boot\x86\pxeboot.com**。|
|[/WdsClientUnattend：<Relative path>]|指定从 remoteInstall 文件夹到自动 Windows 部署服务客户端自动化的无人参与文件的相对路径。|
|[/BootImagepath：<Relative path>]|指定从 remoteInstall 文件夹到此计算机应接收的启动映像的相对路径。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要审批 RequestId 为12的计算机，请键入：
```
wdsutil /Approve-AutoaddDevices /RequestId:12
```
若要批准 Id 为20的计算机并使用指定的设置部署映像，请键入：
```
wdsutil /Approve-AutoaddDevices /RequestId:20 /MachineName:computer1 /OU:OU=Test,CN=company,DC=Domain,DC=Com /User:Domain\User1 
/JoinRights:Full /ReferralServer:MyWDSServer /BootProgram:boot\x86\pxeboot.n12 /WdsClientUnattend:WDSClientUnattend\Unattend.xml /BootImagepath:boot\x86\images\boot.wim
```
若要批准所有挂起的计算机，请键入：
```
wdsutil /verbose /Approve-AutoaddDevices /RequestId:ALL
```
## <a name="additional-references"></a>其他参考
- 使用[AutoaddDevices 命令](using-the-delete-autoadddevices-command.md)
使用[AutoaddDevices](using-the-reject-autoadddevices-command.md)命令
使用[AutoaddDevices 命令](using-the-get-autoadddevices-command.md)的[命令行语法键](command-line-syntax-key.md)

