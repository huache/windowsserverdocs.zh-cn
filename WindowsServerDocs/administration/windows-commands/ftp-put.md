---
title: ftp put
description: Ftp put 命令的参考文章，其中使用当前文件传输类型将本地文件复制到远程计算机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 95cc1e3f-523d-4374-98b8-16e6c276b2ca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/30/2020
ms.openlocfilehash: 5a1a262957177efd6e393f22c9fd9b5541650666
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957579"
---
# <a name="ftp-put"></a>ftp put

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用当前文件传输类型将本地文件复制到远程计算机。

> [!NOTE]
> 此命令与[ftp send 命令](ftp-send_1.md)相同。

## <a name="syntax"></a>语法

```
put <localfile> [<remotefile>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<localfile>` | 指定要复制的本地文件。 |
| `[<remotefile>]` | 指定要在远程计算机上使用的名称。 如果未指定*remotefile*，则该文件将指定*localfile*名称。|

### <a name="examples"></a>示例

若要复制本地文件*test.txt*并将其命名为在远程计算机上*test1.txt* ，请键入：

```
put test.txt test1.txt
```

若要将本地文件*program.exe*复制到远程计算机，请键入：

```
put program.exe
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp ascii 命令](ftp-ascii.md)

- [ftp binary 命令](ftp-binary.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
