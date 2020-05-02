---
title: 设置详细
description: Set verbose 的参考主题，指定在创建卷影副本期间是否提供详细输出。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 93cb93c9-666f-4c74-814b-1c404a949935
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: db31192037e57ee471d04480e0c9333b39e44980
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721895"
---
# <a name="set-verbose"></a>设置详细

指定是否在创建卷影副本期间提供详细输出。 如果不使用参数，则**将 "设置详细**信息" 显示在命令提示符下。

## <a name="syntax"></a>语法

```
set verbose {on | off}
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|-----------|-------------|
|    {on    |    off}     |

## <a name="remarks"></a>备注

-   如果详细模式为 on，则**set**提供有关编写器包含或排除的详细信息，以及元数据压缩和提取的详细信息。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)