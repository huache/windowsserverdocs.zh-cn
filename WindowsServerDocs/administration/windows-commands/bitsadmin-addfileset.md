---
title: bitsadmin addfileset
description: Bitsadmin addfileset 命令的参考文章，它将一个或多个文件添加到指定的作业。
ms.topic: article
ms.assetid: 75466994-262f-4724-b14d-f813c5397675
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 52a97817bd734a06ba787cb6faf17f2a03419da8
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894915"
---
# <a name="bitsadmin-addfileset"></a>bitsadmin addfileset

将一个或多个文件添加到指定的作业。

## <a name="syntax"></a>语法

```
bitsadmin /addfileset <job> <textfile>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| textfile | 一个文本文件，其中每行包含一个远程和一个本地文件名。 **注意：** 名称必须以空格分隔。 以字符开头的行 `#` 被视为注释。 |

## <a name="examples"></a>示例

```
bitsadmin /addfileset files.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
