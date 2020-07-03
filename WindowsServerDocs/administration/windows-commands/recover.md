---
title: recover
description: "\"恢复\" 命令的参考文章，可从错误或有故障的磁盘中恢复可读的信息。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: cf9be2e3-90c8-4773-a201-dc503b91948e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ab7f502b046bf30a40b1fdd386c7faddc5c8f15a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931930"
---
# <a name="recover"></a>recover

从错误或有缺陷的磁盘恢复可读的信息。 此命令读取文件，逐个扇区，并从良好的扇区恢复数据。 坏扇区中的数据将丢失。 由于在您恢复文件时，坏扇区中的所有数据都将丢失，因此，一次只能恢复一个文件。

磁盘准备运行时， **chkdsk**命令报告的坏扇区被标记为 "错误"。 它们不会带来任何风险，**恢复**不会对其造成影响。

## <a name="syntax"></a>语法

```
recover [<drive>:][<path>]<filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| `[<drive>:][<path>]<filename>` | 指定要恢复的文件的名称（如果文件不在当前目录中，则指定文件的位置）。 *Filename*是必需的，不支持通配符。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要恢复驱动器 D 上的*\fiction*目录中的文件*story.txt* ，请键入：

```
recover d:\fiction\story.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
