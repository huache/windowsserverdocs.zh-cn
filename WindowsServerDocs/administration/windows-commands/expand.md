---
title: expand
description: Expand 命令的参考主题，用于扩展一个或多个压缩文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 66de0488-a0c4-40c2-9b03-e40c107ba343
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1204f3db338f835b47db03eab3d178544a6acc85
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83819117"
---
# <a name="expand"></a>expand

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

展开一个或多个压缩文件。 你还可以使用此命令检索分发磁盘中的压缩文件。

还可以使用不同的参数从 Windows 恢复控制台运行**expand**命令。 有关详细信息，请参阅[Windows 恢复环境（WinRE）](https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)。

## <a name="syntax"></a>语法

```
expand [/r] <source> <destination>
expand /r <source> [<destination>]
expand /i <source> [<destination>]
expand /d <source>.cab [/f:<files>]
expand <source>.cab /f:<files> <destination>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /r | 重命名展开的文件。 |
| 源 | 指定要展开的文件。 *源*可以包含驱动器号和冒号、目录名称、文件名或它们的组合。 您可以使用通配符（**&#42;** 或 **？**）。 |
| destination | 指定文件展开的位置。<p>如果*源*包含多个文件并且未指定 **/r**，则*目标*必须是目录。 *目标*可以包含驱动器号和冒号、目录名称、文件名或它们的组合。 目标 `file | path` 规范。 |
| /i | 重命名扩展的文件，但忽略目录结构。 |
| /d | 显示源位置中的文件列表。 不扩展或提取文件。 |
| /f`<files>` | 指定 cab （.cab）文件中要展开的文件。 您可以使用通配符（**&#42;** 或 **？**）。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
