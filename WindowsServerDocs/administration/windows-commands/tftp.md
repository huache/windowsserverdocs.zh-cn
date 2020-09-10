---
title: tftp
description: 在远程计算机之间传输文件。
ms.topic: reference
ms.assetid: 772f19a8-dafe-45cd-878a-f5691f6568ef
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0d2d7c0c62cb0285347e1309f8dadf48a8ef27dc
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640801"
---
# <a name="tftp"></a>tftp

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将文件传输到远程计算机（通常是运行 UNIX 的计算机），该计算机运行的是普通文件传输协议 (tftp) 服务或后台程序。 tftp 通常由在启动过程中从 tftp 服务器检索固件、配置信息或系统映像的嵌入式设备或系统使用。

## <a name="syntax"></a>语法
```
tftp [-i] [<Host>] [{get | put}] <Source> [<Destination>]
```

#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|-i|指定二进制图像传输模式 (也称为八进制模式) 。 在二进制图像模式下，文件以一字节单位传输。 传输二进制文件时，请使用此模式。 如果省略 **-i** ，则文件将在 ASCII 模式下传输。 这是默认传输模式。 此模式将 (EOL 行尾) 字符转换为指定计算机的相应格式。 在传输文本文件时使用此模式。 如果文件传输成功，将显示数据传输速率。|
|\<Host\>|指定本地或远程计算机。|
|put|将本地计算机上的文件 *源* 传输到远程计算机上的文件 *目标* 。 由于 tftp 协议不支持用户身份验证，因此用户必须登录到远程计算机上，并且这些文件必须可在远程计算机上写入。|
|get|将远程计算机上的文件 *目标* 传输到本地计算机上的文件 *源* 。|
|\<Source\>|指定要传输的文件。|
|\<Destination\>|指定文件传输位置。|

## <a name="remarks"></a>备注
-   您可以使用 "添加功能向导" 安装 tftp 客户端。
-   Tftp 协议不支持任何身份验证或加密机制，因此在存在时可能会带来安全风险。 不建议在连接到 Internet 的系统上安装 tftp 客户端。
-   Tftp 客户端是可选软件，在 Windows Vista 和更高版本的 Windows 操作系统上被标记为已弃用。 出于安全原因，Microsoft 不再提供 tftp 服务器服务。

## <a name="examples"></a>示例
从远程计算机**Host1**复制文件 **。**
```
tftp  -i Host1 get boot.img
```

## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
