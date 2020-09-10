---
title: bitsadmin util 和 enableanalyticchannel
description: Bitsadmin util 和 enableanalyticchannel 命令的参考文章，用于启用或禁用 BITS 客户端分析通道。
ms.topic: reference
ms.assetid: 0d7645aa-b91b-4ed7-b630-a1e1be6f6ae9
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 391b53694fcb21d1c17085d487908b090ad88f0a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630563"
---
# <a name="bitsadmin-util-and-enableanalyticchannel"></a>bitsadmin util 和 enableanalyticchannel

启用或禁用 BITS 客户端分析通道。

## <a name="syntax"></a>语法

```
bitsadmin /util /enableanalyticchannel TRUE|FALSE
```

| 参数 | 说明 |
| --------- | ---------- |
| TRUE 或 FALSE | **如果为 TRUE，则** 为指定文件启用内容验证，而 **FALSE** 则禁用。 |

## <a name="examples"></a>示例

启用或禁用 BITS 客户端分析通道。

```
bitsadmin /util / enableanalyticchannel TRUE
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin util 命令](bitsadmin-util.md)

- [bitsadmin 命令](bitsadmin.md)
