---
title: ftp get
description: Ftp get 命令的参考文章，其中使用当前文件传输类型将远程文件复制到本地计算机。
ms.topic: article
ms.assetid: d70355c4-58ef-43e0-916b-c7ecf77e6ee4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: beff912251646bb3c9672921955515247c0b13f3
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87889432"
---
# <a name="ftp-get"></a>ftp get

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将远程文件复制到本地计算机。

> [!NOTE]
> 此命令与 ftp "接收"[命令](ftp-recv.md)相同。

## <a name="syntax"></a>语法

```
get <remotefile> [<localfile>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<remotefile>` | 指定要复制的远程文件。 |
| `[<localfile>]` | 指定要在本地计算机上使用的文件的名称。 如果未指定*localfile* ，则会为该文件提供*remotefile*的名称。 |

### <a name="examples"></a>示例

要使用当前文件传输将*test.txt*复制到本地计算机，请键入：

```
get test.txt
```

要使用当前文件传输*test1.txt*将*test.txt*复制到本地计算机，请键入：

```
get test.txt test1.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp 接收命令](ftp-recv.md)

- [ftp ascii 命令](ftp-ascii.md)

- [ftp binary 命令](ftp-binary.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
