---
title: serverweroptin
description: '* * * * 的参考文章'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f3c0b0af-cafb-4f09-8b36-5a357ddf392d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b8684f448f18ce28e572909fe3958e0e7b6d6a38
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937130"
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

