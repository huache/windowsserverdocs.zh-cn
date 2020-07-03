---
title: AllDevices
description: AllDevices 的参考文章，用于显示所有预留计算机的 Windows 部署服务属性。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5824b3d2-2df1-4ed6-a289-e6c47c13fea2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b5eae53c2dcd39a7f3587f4c3c6bf96d4782ea05
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935220"
---
# <a name="get-alldevices"></a>AllDevices

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示所有预留计算机的 Windows 部署服务属性。 预留计算机是已链接到 active directory 域服务中的计算机帐户的物理计算机。

## <a name="syntax"></a>语法
```
wdsutil [Options] /Get-AllDevices [/forest:{Yes | No}] [/ReferralServer:<Server name>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/forest： {Yes &#124; No}]|指定 Windows 部署服务应返回整个林中的计算机还是本地域中的计算机。 默认设置为 "**否**"，这意味着只会返回本地域中的计算机。|
|[/ReferralServer： <Server name> ]|仅返回为指定服务器预留的那些计算机。|
## <a name="examples"></a>示例
若要查看所有计算机，请键入下列内容之一：
```
wdsutil /Get-AllDevices
wdsutil /verbose /Get-AllDevices /forest:Yes /ReferralServer:MyWDSServer
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[子命令：设置-设备](subcommand-set-device.md) 
[使用 "添加设备" 命令](using-the-add-device-command.md) 
[使用获取设备命令](using-the-get-device-command.md)
