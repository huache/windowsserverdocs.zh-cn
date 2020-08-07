---
title: convert
description: 转换命令的参考文章，可将磁盘从一种磁盘类型转换为另一种类型。
ms.topic: article
ms.assetid: ae151297-af21-4701-bd69-21d775518e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 76990eb33f58b871771e00c9fdef19d5d29c30e8
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87892544"
---
# <a name="convert"></a>convert

将磁盘从一种磁盘类型转换为另一种类型。

## <a name="syntax"></a>语法

```
convert basic
convert dynamic
convert gpt
convert mbr
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| [convert basic 命令](convert-basic.md) | 将空动态磁盘转换为基本磁盘。 |
| [转换动态命令](convert-dynamic.md) | 将基本磁盘转换为动态磁盘。 |
| [转换 gpt 命令](convert-gpt.md) | 将具有主启动记录 (MBR) 分区形式的空白基本磁盘转换为具有 GUID 分区表 (GPT) 分区形式的基本磁盘。 |
| [转换 mbr 命令](convert-mbr.md) | 将具有 GUID 分区表 (GPT) 分区形式的空白基本磁盘转换为具有主启动记录 (MBR) 分区形式的基本磁盘。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
