---
title: convert
description: Convert 命令的参考主题，将磁盘从一种磁盘类型转换为另一种类型。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ae151297-af21-4701-bd69-21d775518e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ab7189ea774750f8de2ceaecd9511fc8c3a71a97
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720737"
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
| [转换 mbr 命令](convert-mbr.md) | 将具有 GUID 分区表（GPT）分区形式的空白基本磁盘转换为具有主启动记录（MBR）分区形式的基本磁盘。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
