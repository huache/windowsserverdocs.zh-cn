---
title: time
description: 了解如何设置和显示系统时间。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1276a257-7283-41da-ae80-fb4cfb311f9d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e27b260bdaa8896ad3cf0ad58294467bbb63e1c2
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721365"
---
# <a name="time"></a>time



显示或设置系统时间。 如果在没有参数的情况下使用， **time**将显示当前系统时间，并提示您输入新时间。



## <a name="syntax"></a>语法

```
time [/t | [<HH>[:<MM>[:<SS>]] [am|pm]]]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<HH> [：\<MM> [：\<SS> [。\<NN>]]] [上午\|am]|将系统时间设置为指定的新时间，其中， *HH*是小时（必需）， *MM*以分钟为单位， *SS*以秒为单位。 *NN*可用于指定百分之几秒。 如果未指定**am**或**pm** ，则默认情况下， **time**使用24小时格式。|
|/t |显示当前时间，而不提示您输入新时间。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   若要更改当前时间，则必须具有管理凭据。
-   必须用冒号（:) 分隔*HH*、 *MM*和*SS*的值。 *SS*和*NN*之间必须用句点（.）分隔。
-   有效的*HH*值为0到24。
-   有效的*MM*和*SS*值为0至59。

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