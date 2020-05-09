---
title: date
description: Date 命令的参考主题，该命令显示或设置系统日期。 如果不使用参数，则
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce6700fb-32f9-4350-a1af-5aee61d4448c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 64d0d94061e1b5c7891b364f4c0fe153b44a564e
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82993203"
---
# <a name="date"></a>date

显示或设置系统日期。 如果在没有参数的情况下使用， **date**将显示当前系统日期设置，并提示你输入新日期。

>[!IMPORTANT]
> 您必须是管理员才能使用此命令。

## <a name="syntax"></a>语法

```
date [/t | <month-day-year>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<month-day-year>` | 设置指定的日期，其中*month*为月份（一位或两位数字，包括值1到12）， *day*为日（一位或两位数字，其中包括值1到31），*年份*是年份（两个或四个数字，其中包括值00到99或1980到2099）。 必须用句点（.）、连字符（-）或正斜杠（/）分隔*月*、*日*和*年*的值。<p>**注意：** 请注意，如果使用2位数表示年份，则值80-99 对应于1980到1999。 |
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

若要保留当前日期并返回到命令提示符，请按**enter**。 若要更改当前日期，请键入新日期，然后按**enter**。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)