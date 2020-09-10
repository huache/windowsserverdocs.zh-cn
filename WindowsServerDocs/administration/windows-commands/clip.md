---
title: clip
description: Clip 命令的参考文章，它将命令行中的命令输出重定向到 Windows 剪贴板。
ms.topic: reference
ms.assetid: 85322d85-3376-4806-845b-93ac77fe27bf
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9f6820d60a8c94ed07bbb23bbbd86be3f1f289b7
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629627"
---
# <a name="clip"></a>clip

将命令行中的命令输出重定向到 Windows 剪贴板。 可以使用此命令将数据直接复制到任何可从剪贴板接收文本的应用程序。 你还可以将此文本输出粘贴到其他程序中。

## <a name="syntax"></a>语法

```
<command> | clip
clip < <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<command>` | 指定要将其输出发送到 Windows 剪贴板的命令。 |
| `<filename>` | 指定要发送到 Windows 剪贴板的内容的文件。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要将当前目录列表复制到 Windows 剪贴板，请键入：

```
dir | clip
```

若 *要将名为* 的程序的输出复制到 Windows 剪贴板，请键入：

```
awk -f generic.awk input.txt | clip
```

若要将名为 *readme.txt* 的文件的内容复制到 Windows 剪贴板，请键入：

```
clip < readme.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)