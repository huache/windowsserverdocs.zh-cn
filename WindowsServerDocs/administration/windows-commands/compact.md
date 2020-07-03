---
title: compact
description: Compact 命令的参考文章，其中显示或更改 NTFS 分区上的文件或目录的压缩。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 429b3752-df0a-43a4-a210-df2f3ad03c3b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c17f7c934ecd4b6988b3ab606059a2acd31b852b
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85929000"
---
# <a name="compact"></a>compact

显示或更改 NTFS 分区上的文件或目录的压缩。 如果在没有参数的情况下使用， **compact**将显示当前目录及其包含的文件的压缩状态。

## <a name="syntax"></a>语法

```
compact [/c | /u] [/s[:<dir>]] [/a] [/i] [/f] [/q] [<filename>[...]]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /c | 压缩指定的目录或文件。 |
| /U | Uncompresses 指定的目录或文件。 |
| /s [： `<dir>` ] | 将**compact**命令应用于指定目录的所有子目录（如果指定了 "无"，则为当前目录）。 |
| /a | 显示隐藏文件或系统文件。 |
| /i | 忽略错误。 |
| /f | 强制对指定目录或文件进行压缩或解压缩。 如果文件是在系统崩溃中断操作中断的情况下进行部分压缩的，则使用 **/f** 。 若要强制完全压缩文件，请使用 **/c**和 **/f**参数，并指定部分压缩的文件。 |
| /q | 仅报告最重要的信息。 |
| `<filename>` | 指定文件或目录。 可以使用多个文件名， **&#42;** 和 **？** 通配符。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 此命令是 NTFS 文件系统压缩功能的命令行版本。 目录的压缩状态指示将文件添加到目录时是否自动对文件进行压缩。 设置目录的压缩状态不一定会更改目录中已有文件的压缩状态。

- 不能使用此命令来读取、写入或装入使用 "磁盘空间管理" 或 DoubleSpace 进行压缩的卷。 还不能使用此命令来压缩文件分配表（FAT）或 FAT32 分区。

## <a name="examples"></a>示例

若要设置当前目录、其子目录和现有文件的压缩状态，请键入：

```
compact /c /s
```

若要设置当前目录中的文件和子目录的压缩状态，而不改变当前目录本身的压缩状态，请键入：

```
compact /c /s *.*
```

若要压缩卷，请在卷的根目录中键入：

```
compact /c /i /s:\
```

> [!NOTE]
> 此示例设置所有目录（包括卷上的根目录）的压缩状态，并压缩卷上的每个文件。 **/I**参数可防止错误消息中断压缩进程。

若要压缩 \tmp 目录和 \tmp 的所有子目录中扩展名为 .bmp 的所有文件，而不修改目录的压缩属性，请键入：

```
compact /c /s:\tmp *.bmp
```

若要强制对在系统崩溃期间部分压缩的文件*zebra.bmp*进行完全压缩，请键入：

```
compact /c /f zebra.bmp
```

若要从目录 c:\tmp 中删除压缩属性，但不更改该目录中任何文件的压缩状态，请键入：

```
compact /u c:\tmp
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)