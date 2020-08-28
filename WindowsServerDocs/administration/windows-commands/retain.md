---
title: retain
description: 保留命令的参考文章，用于准备要用作启动卷或系统卷的现有动态卷。
ms.topic: reference
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 98c27c62ab7e0ac3320986dde6049be40d10db57
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036986"
---
# <a name="retain"></a>retain

准备现有的简单动态卷，用作启动卷或系统卷。 如果使用主启动记录 (MBR) 动态磁盘，则此命令将在主启动记录中创建一个分区条目。 如果使用 GUID 分区表 (GPT) 动态磁盘，则此命令将在 GUID 分区表中创建分区条目。

## <a name="syntax"></a>语法

```
retain
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
