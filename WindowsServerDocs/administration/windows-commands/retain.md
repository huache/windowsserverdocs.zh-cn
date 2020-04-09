---
title: retain
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 891192c0d6b1687cf6bffea0f57d1853e023b776
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835760"
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

