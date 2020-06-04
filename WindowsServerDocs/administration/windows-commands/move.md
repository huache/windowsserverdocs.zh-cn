---
title: 移动
description: Move 命令的参考主题，它将一个或多个文件从一个目录移动到另一个目录。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fde290a8-d385-450f-8987-ee837fed667d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 283ee793769d991c1932eb2271c5117354bdf6a4
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354498"
---
# <a name="move"></a>移动

将一个或多个文件从一个目录移动到另一个目录。

> [!IMPORTANT]
> 将加密文件移动到不支持加密文件系统（EFS）结果的卷将导致错误。 必须首先对文件进行解密，或将其移到支持 EFS 的卷。

## <a name="syntax"></a>语法

```
move [{/y|-y}] [<source>] [<target>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /y | 停止提示确认是否要覆盖现有目标文件。 此参数可在 COPYCMD 环境变量中预设。 您可以使用 **-y**参数覆盖此预设。 除非从批处理脚本中运行该命令，否则默认值为在覆盖文件之前提示。 |
| -y | 开始提示确认是否要覆盖现有目标文件。 |
| `<source>` | 指定要移动的文件的路径和名称。 若要移动或重命名目录，*源*应为当前目录路径和名称。 |
| `<target>` | 指定要将文件移动到的路径和名称。 若要移动或重命名目录，*目标*应该是所需的目录路径和名称。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要将*\Data*目录中扩展名为 .xls 的所有文件移动到*\ Second_Q \reports*目录，请键入：

```
move \data\*.xls \second_q\reports\
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
