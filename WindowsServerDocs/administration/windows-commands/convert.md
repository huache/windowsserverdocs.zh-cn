---
title: convert
description: 转换命令的参考文章，可将磁盘从一种磁盘类型转换为另一种类型。
ms.topic: reference
ms.assetid: ae151297-af21-4701-bd69-21d775518e03
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 654d5266fff3a3fffadb9d176eb07a792f22fa01
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629274"
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
