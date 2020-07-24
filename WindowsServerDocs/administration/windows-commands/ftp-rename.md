---
title: ftp rename
description: 用于重命名远程文件的 ftp rename 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fb613810e764f3dd486ea79869607d68e7f009df
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957439"
---
# <a name="ftp-rename"></a>ftp rename

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

重命名远程文件。

## <a name="syntax"></a>语法

```
rename <filename> <newfilename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<filename>` | 指定要重命名的文件。 |
| `<newfilename>` | 指定新的文件名。 |

### <a name="examples"></a>示例

若要将远程文件*example.txt*重命名为*example1.txt*，请键入：

```
rename example.txt example1.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
