---
title: irftp
description: Irftp 命令的参考文章，可通过红外链接发送文件。
ms.topic: reference
ms.assetid: e15c60a7-546d-4e9f-9871-43aaa1b569d6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c9546dad7bcba60ab73a9bef50c8d4347ef6dc97
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634412"
---
# <a name="irftp"></a>irftp

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过红外链接发送文件。

> [!IMPORTANT]
> 请确保要通过红外链接进行通信的设备启用了红外功能并且工作正常。 此外，请确保在设备之间建立红外链接。

## <a name="syntax"></a>语法

```
irftp [<drive>:\] [[<path>] <filename>] [/h][/s]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>:\` | 指定包含要通过红外链接发送的文件的驱动器。 |
| `[path]<filename>` | 指定要通过红外链接发送的文件或文件集的位置和名称。 如果指定一组文件，则必须指定每个文件的完整路径。 |
| /h | 指定隐藏模式。 当使用隐藏模式时，将在不显示 "无线链接" 对话框的情况下发送文件。 |
| /s | 打开 " **无线链接** " 对话框，以便您可以选择要发送的文件或文件集，而无需使用命令行来指定驱动器、路径和文件名。 如果使用不带任何参数的命令，则 " **无线链接** " 对话框也会打开。 |

### <a name="examples"></a>示例

若要通过红外链接发送 *c:\example.txt* ，请键入：

```
irftp c:\example.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
