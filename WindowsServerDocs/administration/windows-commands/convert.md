---
title: convert
description: 转换命令的参考文章，可将磁盘从一种磁盘类型转换为另一种类型。
ms.topic: reference
ms.assetid: ae151297-af21-4701-bd69-21d775518e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1da57e88027cedac0aad95891720dd3043de2a9d
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030905"
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

| 参数 | 说明 |
| --------- | ----------- |
| [convert basic 命令](convert-basic.md) | 将空动态磁盘转换为基本磁盘。 |
| [转换动态命令](convert-dynamic.md) | 将基本磁盘转换为动态磁盘。 |
| [转换 gpt 命令](convert-gpt.md) | 将具有主启动记录 (MBR) 分区形式的空白基本磁盘转换为具有 GUID 分区表 (GPT) 分区形式的基本磁盘。 |
| [转换 mbr 命令](convert-mbr.md) | 将具有 GUID 分区表 (GPT) 分区形式的空白基本磁盘转换为具有主启动记录 (MBR) 分区形式的基本磁盘。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
