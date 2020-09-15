---
title: tzutil
description: 适用于 tzutil 的参考文章，其中显示 Windows 时区实用程序。
ms.topic: reference
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3640da68f48944fd9d67486dface4cfd77531d57
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078454"
---
# <a name="tzutil"></a>tzutil

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示 Windows 时区实用程序。

## <a name="syntax"></a>语法

```
tzutil [/?] [/g] [/s <timezoneID>[_dstoff]] [/l]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /g | 显示当前时区 ID。 |
| /s `<timezoneID>[_dstoff]` | 使用指定的时区 ID 设置当前时区。 **_Dstoff**后缀禁用时区 (的夏令时调整，) 适用的情况。 值必须用引号括起来。 |
| /l | 列出所有有效的时区 Id 和显示名称。 输出显示为：<ul><li>`<display name>`</li><li>`<time zone ID>`</li></ul> |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

退出代码为 **0** 指示已成功完成命令。

## <a name="examples"></a>示例

若要显示当前时区 ID，请键入：

```
tzutil /g
```

若要将当前时区设置为太平洋标准时间，请键入：

```
tzutil /s "Pacific Standard time"
```

若要将当前时区设置为太平洋标准时间并禁用夏令时调整，请键入：

```
tzutil /s "Pacific Standard time_dstoff"
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
