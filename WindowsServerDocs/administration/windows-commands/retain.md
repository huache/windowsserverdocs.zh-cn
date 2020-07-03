---
title: retain
description: '* * * * 的参考文章'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 958ee0de7bd69c9391407ec6f4a832e1262746a2
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933073"
---
# <a name="retain"></a>retain



准备要用作启动卷或系统卷的现有动态简单卷。

## <a name="syntax"></a>语法

```
retain
```

## <a name="remarks"></a>备注

-   在主启动记录（MBR）动态磁盘上，此命令在主启动记录中创建分区条目。
-   在 GUID 分区表（GPT）动态磁盘上，此命令在 GUID 分区表中创建分区条目。

## <a name="additional-references"></a>其他参考

