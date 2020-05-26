---
title: ftp get
description: Ftp get 命令的参考主题，该主题使用当前文件传输类型将远程文件复制到本地计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d70355c4-58ef-43e0-916b-c7ecf77e6ee4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b7254cac15afc446695f22ee1a63f2f4573d3565
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83819707"
---
# <a name="ftp-get"></a>ftp get

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将远程文件复制到本地计算机。

> [!NOTE]
> 此命令与 ftp "接收"[命令](ftp-recv.md)相同。

## <a name="syntax"></a>语法

```
get <remotefile> [<localfile>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<remotefile>` | 指定要复制的远程文件。 |
| `[<localfile>]` | 指定要在本地计算机上使用的文件的名称。 如果未指定*localfile* ，则会为该文件提供*remotefile*的名称。 |

### <a name="examples"></a>示例

若要使用当前文件传输将*test.txt*复制到本地计算机，请键入：

```
get test.txt
```

若要使用当前文件传输将*test.txt*复制到本地*计算机，请*键入：

```
get test.txt test1.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp 接收命令](ftp-recv.md)

- [ftp ascii 命令](ftp-ascii.md)

- [ftp binary 命令](ftp-binary.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
