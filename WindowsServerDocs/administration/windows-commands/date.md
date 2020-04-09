---
title: date
description: 日期的 Windows 命令主题，用于显示或设置系统日期。 如果不使用参数，则
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ce6700fb-32f9-4350-a1af-5aee61d4448c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8f9e32240eb27d651e324becefd72e9b1a545215
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846740"
---
# <a name="date"></a>date

显示或设置系统日期。 如果在没有参数的情况下使用， **date**将显示当前系统日期设置，并提示你输入新日期。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
date [/t | <Month-Day-Year>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<月-每年 >|设置指定的日期，其中*month*为月份（一位或两位数字）， *day*为日（一位或两位数字），*年份*为年（两位或四位数字）。|
|/t|显示当前日期，而不提示您输入新日期。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   若要更改当前日期，你必须具有管理凭据。
-   必须用句点（.）、连字符（-）或正斜杠（/）分隔*月*、*日*和*年*的值。
-   有效的*月份*值为1到12。
-   有效的*日期*值为1到31。
-   有效的*年份*值为00到99或1980到2099。 如果使用两个数字，则值80到99对应于年份1980到1999。

## <a name="examples"></a><a name=BKMK_examples></a>示例

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
Enter the new date: (mm-dd-yy)
```
若要保留当前日期并返回到命令提示符，请按 ENTER。 若要更改当前日期，请键入新日期，然后按 ENTER。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)