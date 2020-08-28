---
title: serverceipoptin
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 3d7d7fa7-0689-4797-b802-36fe260d21a0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 25a7b116387af973a8c7894edbd0daed0dc59f9a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024961"
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

