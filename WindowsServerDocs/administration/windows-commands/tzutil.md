---
title: tzutil
description: 适用于 tzutil 的参考文章，其中显示 Windows 时区实用程序。
ms.topic: article
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4727423ed6752b3a0c2b578f5838a1108d1d14d4
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87896636"
---
# <a name="tzutil"></a>tzutil

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示 Windows 时区实用程序。

## <a name="syntax"></a>语法
```
tzutil [/?] [/g] [/s <timeZoneID>[_dstoff]] [/l]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/?|在命令提示符下显示帮助。|
|/g|显示当前时区 ID。|
|/s \<timeZoneID> [_dstoff]|使用指定的时区 ID 设置当前时区。 **_Dstoff**后缀禁用时区 (的夏令时调整，) 适用的情况。|
|/l|列出所有有效的时区 Id 和显示名称。 输出将为：<p>-   \<display name><br />-   \<time zone ID>|

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
- [命令行语法项](command-line-syntax-key.md)

