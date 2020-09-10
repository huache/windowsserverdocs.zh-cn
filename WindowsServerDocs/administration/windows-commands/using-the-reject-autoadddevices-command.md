---
title: 拒绝-AutoaddDevices
description: 拒绝-AutoaddDevices 的参考文章，拒绝等待管理审批的计算机。
ms.topic: reference
ms.assetid: ea25a4b2-5fad-4360-9c47-c2c9df7ea31f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 554f3da87ddd3f99284c79614fdde516d171d16d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627917"
---
# <a name="reject-autoadddevices"></a>拒绝-AutoaddDevices

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

拒绝等待管理审批的计算机。 启用自动添加策略后，需要先进行管理审批，然后才能 (未预留的计算机) 可以安装映像。 你可以使用 "服务器 s 属性" 页的 " **PXE 响应** " 选项卡启用此策略。
## <a name="syntax"></a>语法
```
wdsutil [Options] /Reject-AutoaddDevices [/Server:<Server name>] /RequestId:<Request ID or ALL>
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|
|/RequestId： &#124; 所有> <请求 ID|指定分配给挂起计算机的请求 ID。 若要拒绝所有待定计算机，请指定 **all**。|
## <a name="examples"></a>示例
若要拒绝一台计算机，请键入：
```
wdsutil /Reject-AutoaddDevices /RequestId:12
```
若要拒绝所有计算机，请键入：
```
wdsutil /verbose /Reject-AutoaddDevices /Server:MyWDSServer /RequestId:ALL
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AutoaddDevices 命令](using-the-approve-autoadddevices-command.md) 
[使用 AutoaddDevices 命令](using-the-delete-autoadddevices-command.md) 
[使用 AutoaddDevices 命令](using-the-get-autoadddevices-command.md)
