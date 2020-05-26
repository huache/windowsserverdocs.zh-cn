---
title: serverceipoptin
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3d7d7fa7-0689-4797-b802-36fe260d21a0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 45511ee5028779358c77e18c4e1c193dcd86fdfe
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821057"
---
# <a name="serverceipoptin"></a>serverceipoptin

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

允许你参与客户体验改善计划（CEIP）。
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

