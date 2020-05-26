---
title: ftp 重命名
description: Ftp 重命名命令的参考主题，用于重命名远程文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a8d3ea25e48266db6a4a282f2ea395bd8b8d5fd9
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820307"
---
# <a name="ftp-rename"></a>ftp 重命名

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

若要将远程文件*示例 .txt*重命名为*示例 1*，请键入：

```
rename example.txt example1.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
