---
title: ftp 追加
description: Ftp append 命令的参考主题，它使用当前文件类型设置将本地文件追加到远程计算机上的文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7d1b6ab4a6ae0c1654d4335d24f135b2893bdcb7
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83819137"
---
# <a name="ftp-append"></a>ftp 追加

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用 "当前文件类型" 设置将本地文件追加到远程计算机上的文件。

## <a name="syntax"></a>语法

```
append <localfile> [remotefile]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<localfile>` | 指定要添加的本地文件。 |
| [remotefile] | 指定远程计算机上添加的文件 <localfile> 。 如果不使用此参数，则 `<localfile>` 使用该名称代替远程文件名。 |

### <a name="examples"></a>示例

若要将*file1*附加到远程计算机上的*file2* ，请键入：

```
append file1.txt file2.txt
```

将本地*file1*附加到远程计算机上名为*file1*的文件中。

```
append file1.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
