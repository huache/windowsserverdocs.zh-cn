---
title: retain
description: 保留命令的参考文章，用于准备要用作启动卷或系统卷的现有动态卷。
ms.topic: reference
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 201aa8b79f8ac0f89d44be7db3f84c9f3059e206
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626901"
---
# <a name="retain"></a>retain

准备现有的简单动态卷，用作启动卷或系统卷。 如果使用主启动记录 (MBR) 动态磁盘，则此命令将在主启动记录中创建一个分区条目。 如果使用 GUID 分区表 (GPT) 动态磁盘，则此命令将在 GUID 分区表中创建分区条目。

## <a name="syntax"></a>语法

```
retain
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
