---
title: clip
description: Clip 命令的参考主题，该主题将命令行中的命令输出重定向到 Windows 剪贴板。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 85322d85-3376-4806-845b-93ac77fe27bf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 61c905e3dcce52f3a3d35adeac55fc5df574f664
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82712791"
---
# <a name="clip"></a>clip

将命令行中的命令输出重定向到 Windows 剪贴板。 可以使用此命令将数据直接复制到任何可从剪贴板接收文本的应用程序。 你还可以将此文本输出粘贴到其他程序中。

## <a name="syntax"></a>语法

```
<command> | clip
clip < <filename>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<command>` | 指定要将其输出发送到 Windows 剪贴板的命令。 |
| `<filename>` | 指定要发送到 Windows 剪贴板的内容的文件。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要将当前目录列表复制到 Windows 剪贴板，请键入：

```
dir | clip
```

若*要将名为*的程序的输出复制到 Windows 剪贴板，请键入：

```
awk -f generic.awk input.txt | clip
```

若要*将名为 readme.txt 的*文件的内容复制到 Windows 剪贴板，请键入：

```
clip < readme.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)