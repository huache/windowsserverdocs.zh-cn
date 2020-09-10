---
title: ftp send
description: Ftp send 命令的参考文章，其中使用当前文件传输类型将本地文件复制到远程计算机。
ms.topic: reference
ms.assetid: 000aa80a-60a0-4b51-815f-3237a4f3e0f4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: bd2451ba12e2b8017c50bd22df2f61bba253808a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621588"
---
# <a name="ftp-send"></a>ftp send

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将本地文件复制到远程计算机。

> [!NOTE]
> 此命令与 " [ftp put" 命令](ftp-put.md)相同。

## <a name="syntax"></a>语法

```
send <localfile> [<remotefile>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<localfile>` | 指定要复制的本地文件。 |
| `<remotefile>` | 指定要在远程计算机上使用的名称。 如果未指定 *remotefile*，则文件将获取 *localfile* 名称。 |

### <a name="examples"></a>示例

若要复制本地文件 *test.txt* 并将其命名为在远程计算机上 *test1.txt* ，请键入：

```
send test.txt test1.txt
```

若要将本地文件 *program.exe* 复制到远程计算机，请键入：

```
send program.exe
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
