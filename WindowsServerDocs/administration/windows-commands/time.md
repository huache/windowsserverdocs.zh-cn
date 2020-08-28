---
title: time
description: 了解如何设置和显示系统时间。
ms.topic: reference
ms.assetid: 1276a257-7283-41da-ae80-fb4cfb311f9d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ca279bfacbc3fab3c1a4b56f33f5000fcab9d589
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024531"
---
# <a name="time"></a>time



显示或设置系统时间。 如果在没有参数的情况下使用， **time** 将显示当前系统时间，并提示您输入新时间。



## <a name="syntax"></a>语法

```
time [/t | [<HH>[:<MM>[:<SS>]] [am|pm]]]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<HH>[:\<MM>[:\<SS>[.\<NN>]]][上午 am \| ]|将系统时间设置为指定的新时间，其中， *HH* 以小时为单位 (必需) ， *MM* 为分钟， *SS* 以秒为单位。 *NN* 可用于指定百分之几秒。 如果未指定 **am** 或 **pm** ，则默认情况下， **time** 使用24小时格式。|
|/t |显示当前时间，而不提示您输入新时间。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>注解

-   若要更改当前时间，则必须具有管理凭据。
-   必须用冒号分隔 *HH*、 *MM*和 *SS* 的值 (： ) 。 *SS* 和 *NN* 必须用句点 ( 分隔。 ) 。
-   有效的 *HH* 值为0到24。
-   有效的 *MM* 和 *SS* 值为0至59。

## <a name="examples"></a><a name="BKMK_examples"></a>示例

如果启用了命令扩展，若要显示当前系统时间，请键入：
```
time /t
```
若要将当前系统时间更改为 5:30 P.M.，请键入以下内容之一：
```
time 17:30:00
time 5:30 pm
```
若要显示当前系统时间，后跟输入新时间的提示，请键入：
```
The current time is: 17:33:31.35
Enter the new time:
```
若要保留当前时间并返回到命令提示符，请按 ENTER。 若要更改当前时间，请键入新时间，然后按 ENTER。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)