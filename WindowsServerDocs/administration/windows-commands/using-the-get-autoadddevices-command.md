---
title: AutoaddDevices
description: AutoaddDevices 的参考文章，其中显示了在 Windows 部署服务服务器上自动添加数据库中的所有计算机。
ms.topic: article
ms.assetid: 24b4b688-55b0-4bd9-a2f5-7ef4b3dfe2f2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6e9fcb25f465cdb26112a48e25c856a42dd21326
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87892467"
---
# <a name="get-autoadddevices"></a>AutoaddDevices

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示 Windows 部署服务服务器上自动添加数据库中的所有计算机。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```
### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
|/Devicetype： {PendingDevices &#124; RejectedDevices &#124; ApprovedDevices}|指定要返回的计算机的类型。<p>-   **PendingDevices**返回数据库中状态为 "挂起" 的所有计算机。<br />-   **RejectedDevices**返回数据库中状态为 "已拒绝" 的所有计算机。<br />-   **ApprovedDevices**返回数据库中状态为 "已批准" 的所有计算机。|
## <a name="examples"></a>示例
若要查看所有批准的计算机，请键入：
```
wdsutil /Get-AutoaddDevices /Devicetype:ApprovedDevices
```
若要查看所有拒绝的计算机，请键入：
```
wdsutil /verbose /Get-AutoaddDevices /Devicetype:RejectedDevices /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AutoaddDevices 命令](using-the-delete-autoadddevices-command.md) 
[使用 AutoaddDevices 命令](using-the-approve-autoadddevices-command.md) 
[使用 AutoaddDevices 命令](using-the-reject-autoadddevices-command.md)
