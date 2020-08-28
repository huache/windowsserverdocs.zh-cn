---
title: bitsadmin addfileset
description: Bitsadmin addfileset 命令的参考文章，它将一个或多个文件添加到指定的作业。
ms.topic: reference
ms.assetid: 75466994-262f-4724-b14d-f813c5397675
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2b9b93f38f3604c4f0a9fcaf886d74356d355086
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033705"
---
# <a name="bitsadmin-addfileset"></a>bitsadmin addfileset

将一个或多个文件添加到指定的作业。

## <a name="syntax"></a>语法

```
bitsadmin /addfileset <job> <textfile>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
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
