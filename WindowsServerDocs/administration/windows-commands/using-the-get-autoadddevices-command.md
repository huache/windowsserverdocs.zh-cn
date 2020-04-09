---
title: AutoaddDevices
description: 用于 AutoaddDevices 的 Windows 命令主题，其中显示了位于 Windows 部署服务服务器上自动添加数据库中的所有计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 24b4b688-55b0-4bd9-a2f5-7ef4b3dfe2f2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b373fca81769ff1296d0e9a0788fe536c4fc3132
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831180"
---
# <a name="get-autoadddevices"></a>AutoaddDevices

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

显示 Windows 部署服务服务器上自动添加数据库中的所有计算机。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
|/Devicetype： {PendingDevices &#124; RejectedDevices &#124; ApprovedDevices}|指定要返回的计算机的类型。<p>-   **PendingDevices**返回数据库中状态为 "挂起" 的所有计算机。<br />-   **RejectedDevices**返回数据库中状态为 "已拒绝" 的所有计算机。<br />-   **ApprovedDevices**返回数据库中状态为 "已批准" 的所有计算机。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要查看所有批准的计算机，请键入：
```
wdsutil /Get-AutoaddDevices /Devicetype:ApprovedDevices
```
若要查看所有拒绝的计算机，请键入：
```
wdsutil /verbose /Get-AutoaddDevices /Devicetype:RejectedDevices /Server:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- 使用[AutoaddDevices 命令](using-the-delete-autoadddevices-command.md)
使用 AutoaddDevices 命令
使用[Using The Reject-AutoaddDevices Command](using-the-reject-autoadddevices-command.md) [命令的](using-the-approve-autoadddevices-command.md)[命令行语法键](command-line-syntax-key.md)

