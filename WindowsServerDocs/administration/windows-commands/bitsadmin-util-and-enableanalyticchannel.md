---
title: bitsadmin util 和 enableanalyticchannel
description: Bitsadmin util 和 enableanalyticchannel 命令的参考文章，用于启用或禁用 BITS 客户端分析通道。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0d7645aa-b91b-4ed7-b630-a1e1be6f6ae9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 515402f42dee54baa662f37718841f70b1cd2882
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927419"
---
# <a name="bitsadmin-util-and-enableanalyticchannel"></a>bitsadmin util 和 enableanalyticchannel

启用或禁用 BITS 客户端分析通道。

## <a name="syntax"></a>语法

```
bitsadmin /util /enableanalyticchannel TRUE|FALSE
```

| 参数 | 说明 |
| --------- | ---------- |
| TRUE 或 FALSE | **如果为 TRUE，则**为指定文件启用内容验证，而**FALSE**则禁用。 |

## <a name="examples"></a>示例

启用或禁用 BITS 客户端分析通道。

```
bitsadmin /util / enableanalyticchannel TRUE
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin util 命令](bitsadmin-util.md)

- [bitsadmin 命令](bitsadmin.md)
