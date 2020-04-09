---
title: convert
description: 用于转换的 Windows 命令主题，将磁盘从一种磁盘类型转换为另一种类型。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ae151297-af21-4701-bd69-21d775518e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b1b5c62b7e51b497faac77a13185f844de230d67
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80847180"
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

|参数|说明|
|---------|-----------|
|[转换基本](convert-basic.md)|将空的动态磁盘转换为基本磁盘。|
|[转换动态](convert-dynamic.md)|将基本磁盘转换为动态磁盘。|
|[转换 gpt](convert-gpt.md)|将具有主启动记录 (MBR) 分区形式的空白基本磁盘转换为具有 GUID 分区表 (GPT) 分区形式的基本磁盘。|
|[转换 mbr](convert-mbr.md)|将具有 GUID 分区表（GPT）分区形式的空白基本磁盘转换为具有主启动记录（MBR）分区形式的基本磁盘。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

