---
title: tzutil
description: 适用于 tzutil 的参考主题，其中显示 Windows 时区实用程序。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4011f04b762522c8c0d157993bad71d88758d32f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721205"
---
# <a name="tzutil"></a>tzutil

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示 Windows 时区实用程序。 

## <a name="syntax"></a>语法
```
tzutil [/?] [/g] [/s <timeZoneID>[_dstoff]] [/l]
```
#### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|/?|在命令提示符下显示帮助。|
|/g|显示当前时区 ID。|
|/s \<timeZoneID> [_dstoff]|使用指定的时区 ID 设置当前时区。 **_Dstoff**后缀为时区禁用夏令时调整（如果适用）。|
|/l|列出所有有效的时区 Id 和显示名称。 输出将为：<p>-   \<显示名称><br />-   \<时区 ID>|

## <a name="remarks"></a>备注
退出代码为**0**指示已成功完成命令。

## <a name="examples"></a>示例
若要显示当前时区 ID，请键入：
```
tzutil /g
```
若要将当前时区设置为太平洋标准时间，请键入：
```
tzutil /s Pacific Standard time
```
若要将当前时区设置为太平洋标准时间并禁用夏令时调整，请键入：
```
tzutil /s Pacific Standard time_dstoff
```
## <a name="additional-references"></a>其他参考
-   - [命令行语法项](command-line-syntax-key.md)

