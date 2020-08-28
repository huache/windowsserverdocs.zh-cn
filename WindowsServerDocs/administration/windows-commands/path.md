---
title: path
description: 参考文章：在 PATH 环境变量中设置命令路径，指定用于搜索可执行文件 () 文件的目录集。
ms.topic: reference
ms.assetid: 1bfa1349-e79a-472b-a9e6-d7a91149ae8f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fe60518a70f4fdc9992f70b3b561b067404a31f1
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032504"
---
# <a name="path"></a>path

在 PATH 环境变量中设置命令路径，指定用于搜索可执行文件 () 文件的目录集。 如果不使用参数，则此命令将显示当前命令路径。

## <a name="syntax"></a>语法

```
path [[<drive>:]<path>[;...][;%PATH%]]
path ;
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `[<drive>:]<path>` | 指定要在命令路径中设置的驱动器和目录。 当前目录始终在命令路径中指定的目录之前搜索。 |
| ; | 分隔命令路径中的目录。 如果在不使用其他参数的情况下使用， **则为;** 从 PATH 环境变量中清除现有命令路径，并指示 Cmd.exe 仅在当前目录中进行搜索。 |
| `%PATH%` | 将命令路径追加到 PATH 环境变量中列出的现有目录集。 如果包含此参数，Cmd.exe 会将其替换为 PATH 环境变量中的命令路径值，从而无需在命令提示符下手动输入这些值。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="remarks"></a>注解


- Windows 操作系统使用默认文件扩展名按以下优先级顺序进行搜索： .exe、.com、.bat 和 .cmd。 这意味着，如果你要查找名为的批处理文件，acct.bat 但在同一目录中有一个名为 acct.exe 的应用，则必须在命令提示符下包含 .bat 扩展名。

- 如果命令路径中的两个或多个文件具有相同的文件名和扩展名，则此命令将首先在当前目录中搜索指定的文件名。 然后，它将按照路径环境变量中列出的顺序搜索命令路径中的目录。

- 如果将 **path** 命令放在 autoexec.bat 文件中，则每次登录到计算机时，Windows 操作系统会自动追加指定的 MS-DOS 子系统搜索路径。 Cmd.exe 不使用 Autoexec.bat 文件。 从快捷方式开始时，Cmd.exe 继承在我的电脑/Properties/Advanced/环境中设置的环境变量。

## <a name="examples"></a>示例

若要在路径 *c:\user\taxes*、 *b:\user\invest*和 *b:\bin* 中搜索外部命令，请键入：

```
path c:\user\taxes;b:\user\invest;b:\bin
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
