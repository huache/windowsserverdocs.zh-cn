---
title: recover
description: "\"恢复\" 命令的参考文章，可从错误或有故障的磁盘中恢复可读的信息。"
ms.topic: reference
ms.assetid: cf9be2e3-90c8-4773-a201-dc503b91948e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9bb402c5821ae8caa0a83d132a7fbeef9c88b4bd
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637303"
---
# <a name="recover"></a>recover

从错误或有缺陷的磁盘恢复可读的信息。 此命令读取文件，逐个扇区，并从良好的扇区恢复数据。 坏扇区中的数据将丢失。 由于在您恢复文件时，坏扇区中的所有数据都将丢失，因此，一次只能恢复一个文件。

磁盘准备运行时， **chkdsk** 命令报告的坏扇区被标记为 "错误"。 它们不会带来任何风险， **恢复** 不会对其造成影响。

## <a name="syntax"></a>语法

```
recover [<drive>:][<path>]<filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `[<drive>:][<path>]<filename>` | 指定文件名 (和文件的位置（如果文件不在当前目录中，则为要恢复) 。 *Filename* 是必需的，不支持通配符。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要恢复驱动器 D 上的*\fiction*目录中的文件*story.txt* ，请键入：

```
recover d:\fiction\story.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
