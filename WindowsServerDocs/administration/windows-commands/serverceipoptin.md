---
title: serverceipoptin
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 3d7d7fa7-0689-4797-b802-36fe260d21a0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 691b2e072d6581f8f8760e20d4ba8f09500ed169
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638976"
---
# <a name="serverceipoptin"></a>serverceipoptin

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

允许 (CEIP) 参与客户体验改善计划。
## <a name="syntax"></a>语法
```
serverceipoptin [/query] [/enable] [/disable]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/query|验证当前设置。|
|/enable|启用参与。|
|/disable|禁用参与。|
|/?|在命令提示符下显示帮助。|
## <a name="examples"></a>示例
若要验证当前设置，请键入：
```
serverceipoptin /query
```
若要启用参与，请键入：
```
serverceipoptin /enable
```
若要禁用参与，请键入：
```
serverceipoptin /disable
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)

