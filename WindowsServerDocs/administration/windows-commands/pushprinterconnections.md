---
title: pushprinterconnections
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c30afb97-b149-478f-a4b9-2cbc25361818 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5941b1eba55ce7524946f3257c093d409ef7d773
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837070"
---
# <a name="pushprinterconnections"></a>pushprinterconnections



从组策略读取已部署的打印机连接设置，并根据需要部署/删除打印机连接。

## <a name="syntax"></a>语法

```
pushprinterconnections <-log> <-?>
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|< 日志 >|将每个用户的调试日志文件写入% temp，或将每个计算机的调试日志写入%windir%\temp|
|<-？ >|在命令提示符处显示帮助。|

## <a name="remarks"></a>备注

此实用程序在计算机启动或用户登录脚本中使用，不能从命令行运行。

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [使用组策略部署打印机](https://go.microsoft.com/fwlink/?LinkId=230627)