---
title: unlodctr
description: Unlodctr 的参考文章，用于从系统注册表中删除服务或设备驱动程序的性能计数器名称和说明文本
ms.topic: reference
ms.assetid: fc8aa6f0-c1d9-47ea-937a-28152148e774
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e0494d0b4509c4b75af9ca8473e3ae65353e02c1
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626568"
---
# <a name="unlodctr"></a>unlodctr

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

从系统注册表中删除服务或设备驱动程序的 **性能计数器** 名称和 **说明** 文本。

## <a name="syntax"></a>语法
```
Unlodctr <DriverName>
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|\<DriverName>|从 Windows Server 2003 注册表删除驱动程序或服务的性能计数器名称设置和说明文本 <DriverName> 。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
> [!WARNING]
> 不正确地编辑注册表可能会对系统造成严重损坏。 在更改注册表之前，应备份计算机上任何有价值的数据。

如果提供的信息包含空格，请使用引号将文本括 (例如 <DriverName>) 。

## <a name="examples"></a>示例
若要删除 (SMTP) 服务的简单邮件传输协议的当前性能注册表设置和计数器说明文本，请执行以下操作：
```
unlodctr SMTPSVC
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)

