---
title: bitsadmin setvalidationstate
description: 适用于 bitsadmin setvalidationstate 的 Windows 命令主题，用于设置作业中给定文件的内容验证状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e8fc8e8c-171c-4681-8057-6986b018e576
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: de6480596b55b3a483076297f32ce52a975915db
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849110"
---
# <a name="bitsadmin-setvalidationstate"></a>bitsadmin setvalidationstate

设置作业中给定文件的内容验证状态。

## <a name="syntax"></a>语法

```
bitsadmin /SetValidationState <Job> <file index> <true|false> 
```

### <a name="parameters"></a>参数

| 参数  |          说明           |
|------------|--------------------------------|
|    作业     | 该作业的显示名称或 GUID |
| 文件索引 |         从0开始          |
|    True    |             False              |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将名为*myJob*的作业的文件2的内容验证状态设置为 TRUE。
```
C:\>bitsadmin /SetValidationState myJob 2 TRUE 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)