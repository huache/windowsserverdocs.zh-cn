---
title: serverweroptin
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f3c0b0af-cafb-4f09-8b36-5a357ddf392d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6329552d3525a1330286e04c6400378b14039fbf
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821259"
---
# <a name="serverweroptin"></a>serverweroptin

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

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

