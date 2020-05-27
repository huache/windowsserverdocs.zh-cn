---
title: exit
description: Exit 的参考主题，用于退出命令解释器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d3cee4a2-6210-46f0-b8e4-7381c3c4e530
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fdfec9861e63f7484a9c45c45a22d19873cabbe9
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83819497"
---
# <a name="exit"></a>exit

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

退出命令解释器或当前批处理脚本。

## <a name="syntax"></a>语法

```
exit [/b] [<exitcode>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /b | 退出当前的批处理脚本，而不是退出 Cmd.exe。 如果从批处理脚本外部执行，则退出 Cmd.exe。 |
| `<exitcode>` | 指定数值。 如果指定了 **/b** ，则 ERRORLEVEL 环境变量设置为该数字。 如果要退出命令解释器，则进程退出代码将设置为该数字。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要关闭命令解释器，请键入：

```
exit
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
