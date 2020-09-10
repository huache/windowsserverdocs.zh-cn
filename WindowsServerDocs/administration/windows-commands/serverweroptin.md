---
title: serverweroptin
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: f3c0b0af-cafb-4f09-8b36-5a357ddf392d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 73bdce2a4b18f55239b61132df0417b02cb683c2
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637779"
---
# <a name="serverweroptin"></a>serverweroptin

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

允许你启用错误报告。
## <a name="syntax"></a>语法
```
serverweroptin [/query] [/detailed] [/summary]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/query|验证当前设置。|
|/detailed|自动发送详细报告。|
|/summary|自动发送摘要报告。|
|/?|在命令提示符下显示帮助。|
## <a name="examples"></a>示例
若要验证当前的设置，请键入：
```
serverweroptin /query
```
若要自动发送详细报告，请键入：
```
serverweroptin /detailed
```
若要自动发送摘要报告，请键入
```
serverweroptin /summary
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)

