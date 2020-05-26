---
title: ftp 发送
description: Ftp send 命令的参考主题，它使用当前文件传输类型将本地文件复制到远程计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 000aa80a-60a0-4b51-815f-3237a4f3e0f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 12ce45a0eb26e1aa4a0d7daace831751e1b67f4a
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820297"
---
# <a name="ftp-send"></a>ftp 发送

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

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
| `<remotefile>` | 指定要在远程计算机上使用的名称。 如果未指定*remotefile*，则文件将获取*localfile*名称。 |

### <a name="examples"></a>示例

若要复制本地文件*test.txt*并将其命名为*test1* ，请在远程计算机上键入：

```
send test.txt test1.txt
```

若要将本地文件*program*复制到远程计算机，请键入：

```
send program.exe
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
