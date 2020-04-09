---
title: 设置详细
description: 设置详细的 Windows 命令主题，它指定在创建卷影副本期间是否提供详细输出。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 93cb93c9-666f-4c74-814b-1c404a949935
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f06400259004095fcc4ec81b2ed3cb25678a4b7d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834460"
---
# <a name="set-verbose"></a>设置详细

指定是否在创建卷影副本期间提供详细输出。 如果不使用参数，则**将 "设置详细**信息" 显示在命令提示符下。

## <a name="syntax"></a>语法

```
set verbose {on | off}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|-----------|-------------|
|    {on    |    off}     |

## <a name="remarks"></a>备注

-   如果详细模式为 on，则**set**提供有关编写器包含或排除的详细信息，以及元数据压缩和提取的详细信息。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)