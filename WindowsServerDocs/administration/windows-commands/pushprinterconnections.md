---
title: pushprinterconnections
description: Pushprinterconnections.exe 命令的参考文章，其中从组策略读取已部署的打印机连接设置，并根据需要部署/删除打印机连接。
ms.topic: reference
ms.assetid: c30afb97-b149-478f-a4b9-2cbc25361818
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 41ed8af3b4d70058887de10215f36e1aa530e912
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032367"
---
# <a name="pushprinterconnections"></a>pushprinterconnections

从组策略读取已部署的打印机连接设置，并根据需要部署/删除打印机连接。

> [!IMPORTANT]
> 此实用程序在计算机启动或用户登录脚本中使用，不应从命令行运行。

## <a name="syntax"></a>语法

```
pushprinterconnections <-log> <-?>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| < 日志> | 将每个用户的调试日志文件写入 *% temp*，或将每个计算机的调试日志写入 *%windir%\temp*。 |
| <-？ > | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)

- [使用组策略部署打印机](https://go.microsoft.com/fwlink/?LinkId=230627)
