---
title: ftp mput
description: Ftp mput 命令的参考文章，其中使用当前文件传输类型将本地文件复制到远程计算机。
ms.topic: reference
ms.assetid: 980f15e7-7cf1-4813-9946-a8cc4edfb198
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: cd799e713b71f23c7ce22a9ee81dc19cd78f8c31
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635316"
---
# <a name="ftp-mput"></a>ftp mput

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将本地文件复制到远程计算机。

## <a name="syntax"></a>语法

```
mput <localfile>[ ]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<localfile>` | 指定要复制到远程计算机的本地文件。 |

### <a name="examples"></a>示例

要使用当前文件传输类型将 *Program1.exe* 和 *Program2.exe* 复制到远程计算机，请键入：

```
mput Program1.exe Program2.exe
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp ascii 命令](ftp-ascii.md)

- [ftp binary 命令](ftp-binary.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
