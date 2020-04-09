---
title: 拒绝-AutoaddDevices
description: 拒绝-AutoaddDevices 的 Windows 命令主题，拒绝等待管理审批的计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ea25a4b2-5fad-4360-9c47-c2c9df7ea31f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 39bdddbbc169a0a0810fcc67e95224360858b728
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830650"
---
# <a name="reject-autoadddevices"></a>拒绝-AutoaddDevices

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

拒绝等待管理审批的计算机。 启用自动添加策略后，在未知计算机（未预留的计算机）之前需要管理审批才能安装映像。 你可以使用 "服务器 s 属性" 页的 " **PXE 响应**" 选项卡启用此策略。
## <a name="syntax"></a>语法
```
wdsutil [Options] /Reject-AutoaddDevices [/Server:<Server name>] /RequestId:<Request ID or ALL>
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|
|/RequestId： < 请求 ID &#124;全部 >|指定分配给挂起计算机的请求 ID。 若要拒绝所有待定计算机，请指定**all**。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要拒绝一台计算机，请键入：
```
wdsutil /Reject-AutoaddDevices /RequestId:12
```
若要拒绝所有计算机，请键入：
```
wdsutil /verbose /Reject-AutoaddDevices /Server:MyWDSServer /RequestId:ALL
```
## <a name="additional-references"></a>其他参考
- 使用[AutoaddDevices 命令](using-the-approve-autoadddevices-command.md)的[命令行语法键](command-line-syntax-key.md)

使用[AutoaddDevices 命令](using-the-get-autoadddevices-command.md)
使用[AutoaddDevices 命令](using-the-delete-autoadddevices-command.md)
