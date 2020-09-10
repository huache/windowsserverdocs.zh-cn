---
title: date
description: 日期命令的参考文章，其中显示或设置系统日期。 如果不使用参数，则
ms.topic: reference
ms.assetid: ce6700fb-32f9-4350-a1af-5aee61d4448c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ca9e8b9305132e9af03308d2e0ca0cc20ed89469
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628969"
---
# <a name="date"></a>date

显示或设置系统日期。 如果在没有参数的情况下使用， **date** 将显示当前系统日期设置，并提示你输入新日期。

>[!IMPORTANT]
> 您必须是管理员才能使用此命令。

## <a name="syntax"></a>语法

```
date [/t | <month-day-year>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<month-day-year>` | 设置指定的日期，其中 *month* 是月份 (一位或两位数字，其中包括值1到 12) ， *day* 是 (一位或两位数字的日期，包括值1到 31) ， *年份* 是 (两个或四个数字的年份，其中包括值00到99或1980到 2099) 。 必须将 *月*、 *日*和 *年* 的值分别用句点 (. ) 、连字符 (-) 或斜线标记 (/) 分隔开。<p>**注意：** 请注意，如果使用2位数表示年份，则值80-99 对应于1980到1999。 |
| /t  | 显示当前日期，而不提示您输入新日期。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

如果启用了命令扩展，若要显示当前系统日期，请键入：

```
date /t
```

若要将当前系统日期更改为2007年8月3日，可以键入以下任何内容：

```
date 08.03.2007
date 08-03-07
date 8/3/07
```

若要显示当前系统日期，然后输入新日期的提示，请键入：

```
The current date is: Mon 04/02/2007
Enter the new date: (mm-dd-yyyy)
```

若要保留当前日期并返回到命令提示符，请按 **enter**。 若要更改当前日期，请键入新日期，然后按 **enter**。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)