---
title: 添加设备
description: 用于在 active directory 域服务中其预留计算机的添加设备的参考文章。 预留计算机也称为已知计算机。
ms.topic: reference
ms.assetid: 1e599cc4-464a-421b-b6bb-c101af154131
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 89713dbfa28e552fa78a619bc5f5337d65460f22
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024521"
---
# <a name="add-device"></a>添加设备

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在 active directory 域服务中其预留一台计算机。 预留计算机也称为已知计算机。 这允许你配置属性来控制客户端的安装。 例如，你可以配置网络启动程序和客户端应接收的无人参与文件，以及客户端应从中下载网络启动程序的服务器。

## <a name="syntax"></a>语法
```
wdsutil /add-Device /Device:<Device name> /ID:<UUID | MAC address> [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>]
[/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relative path>] [/OU:<DN of OU>] [/Domain:<Domain>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|装置<computer name>|指定要添加的计算机的名称。|
|/ID： <UUID &#124; MAC 地址>|指定计算机的 GUID/UUID 或 MAC 地址。 GUID/UUID 必须采用以下两种格式之一：二进制字符串或 GUID 字符串。 例如：<p>二进制字符串： **/id： ACEFA3E81F20694E953EB2DAA1E8B1B6**<p>GUID 字符串： **/id： E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6**<p>MAC 地址必须采用以下格式： **00B056882FDC** (没有短划线) 或 00-)  (**2f** ----|
|[/ReferralServer： <Server name> ]|指定要连接的服务器的名称，以使用普通文件传输协议 (tftp) 下载网络启动程序和启动映像。|
|[/BootProgram： <Relative path> ]|指定从 remoteInstall 文件夹到此计算机应接收的网络引导程序的相对路径。 例如： boot\x86\pxeboot.com|
|[/WdsClientUnattend： <Relative path> ]|指定从 remoteInstall 文件夹到无人参与安装文件的相对路径，该文件自动执行 Windows 部署服务客户端的安装屏幕。|
|[/User： <Domain\User &#124; User@Domain>]|设置计算机帐户对象的权限，以向指定的用户授予将计算机加入域所需的权限。|
|[/JoinRights： {JoinOnly &#124; Full}]|指定要分配给用户的权限类型。<p>-   **JoinOnly** 要求管理员重置计算机帐户，然后用户才能将计算机加入域。<br />-   **Full** 为用户提供完全访问权限，包括将计算机加入域的权限。|
|[/JoinDomain： {Yes &#124; No}]|指定是否应在操作系统安装过程中将计算机加入域作为此计算机帐户。 默认值为 **"是"**。|
|[/BootImagepath： <Relative path> ]|指定从 remoteInstall 文件夹到此计算机应使用的启动映像的相对路径。|
|[/OU： <DN of OU> ]|应在其中创建计算机帐户对象的组织单位的可分辨名称。 例如： **OU = MyOU，CN = Test，dc = Domain，DC = com**。 默认位置是默认的计算机容器。|
|[/Domain： <Domain> ]|应在其中创建计算机帐户对象的域。 默认位置是本地域。|
## <a name="examples"></a>示例
若要使用 MAC 地址添加计算机，请键入：
```
wdsutil /add-Device /Device:computer1 /ID:00-B0-56-88-2F-DC
```
若要使用 GUID 字符串添加计算机，请键入：
```
wdsutil /add-Device /Device:computer1 /ID:{E8A3EFAC-201F-4E69-953F-B2DAA1E8B1B6} /ReferralServer:WDSServer1 /BootProgram:boot\x86\pxeboot.com
/WDSClientUnattend:WDSClientUnattend\unattend.xml /User:Domain\MyUser/JoinRights:Full /BootImagepath:boot\x86\images\boot.wim /OU:OU=MyOU,CN=Test,DC=Domain,DC=com
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AllDevices 命令](using-the-get-alldevices-command.md) 
[使用获取设备命令](using-the-get-device-command.md) 
[子命令：设置-设备](subcommand-set-device.md) 
[新-WdsClient](/previous-versions/windows/powershell-scripting/dn283430(v=wps.630))
