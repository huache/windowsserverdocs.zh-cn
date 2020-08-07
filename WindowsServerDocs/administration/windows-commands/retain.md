---
title: retain
description: '* * * * 的参考文章'
ms.topic: article
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9a0205f3b67bd99ca590c7ffc6fbd04b0eefd94f
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87883648"
---
# <a name="retain"></a>retain



准备要用作启动卷或系统卷的现有动态简单卷。

## <a name="syntax"></a>语法

```
retain
```

## <a name="remarks"></a>备注

-   在主启动记录 (MBR) 动态磁盘上，此命令在主启动记录中创建分区条目。
-   在 GUID 分区表 (GPT) 动态磁盘上，此命令在 GUID 分区表中创建分区条目。

## <a name="additional-references"></a>其他参考

