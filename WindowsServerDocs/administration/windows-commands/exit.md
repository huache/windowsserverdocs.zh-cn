---
title: exit
description: 退出命令解释器的参考文章。
ms.topic: reference
ms.assetid: d3cee4a2-6210-46f0-b8e4-7381c3c4e530
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c1fbf37b80c55a9620c2e72d20ea13c6766b7da9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635952"
---
# <a name="exit"></a>exit

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

退出命令解释器或当前批处理脚本。

## <a name="syntax"></a>语法

```
exit [/b] [<exitcode>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /b | 退出当前批处理脚本，而不是退出 Cmd.exe。 如果从批处理脚本外部执行，则退出 Cmd.exe。 |
| `<exitcode>` | 指定数值。 如果指定了 **/b** ，则 ERRORLEVEL 环境变量设置为该数字。 如果要退出命令解释器，则进程退出代码将设置为该数字。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要关闭命令解释器，请键入：

```
exit
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
