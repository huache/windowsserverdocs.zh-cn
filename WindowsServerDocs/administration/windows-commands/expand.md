---
title: expand
description: 展开命令的参考文章，用于扩展一个或多个压缩文件。
ms.topic: article
ms.assetid: 66de0488-a0c4-40c2-9b03-e40c107ba343
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e1359c6db46095bd472a20e946b8748a64eb4d14
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890414"
---
# <a name="expand"></a>expand

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

展开一个或多个压缩文件。 你还可以使用此命令检索分发磁盘中的压缩文件。

还可以使用不同的参数从 Windows 恢复控制台运行**expand**命令。 有关详细信息，请参阅[Windows 恢复环境 (WinRE) ](/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)。

## <a name="syntax"></a>语法

```
expand [/r] <source> <destination>
expand /r <source> [<destination>]
expand /i <source> [<destination>]
expand /d <source>.cab [/f:<files>]
expand <source>.cab /f:<files> <destination>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| /r | 重命名展开的文件。 |
| source | 指定要展开的文件。 *源*可以包含驱动器号和冒号、目录名称、文件名或它们的组合。  (**&#42;** 或 **？**) ，可以使用通配符。 |
| 目标 | 指定文件展开的位置。<p>如果*源*包含多个文件并且未指定 **/r**，则*目标*必须是目录。 *目标*可以包含驱动器号和冒号、目录名称、文件名或它们的组合。 目标 `file | path` 规范。 |
| /i | 重命名扩展的文件，但忽略目录结构。 |
| /d | 显示源位置中的文件列表。 不扩展或提取文件。 |
| /f`<files>` | 指定要扩展的 cabinet ( .cab) 文件中的文件。  (**&#42;** 或 **？**) ，可以使用通配符。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
