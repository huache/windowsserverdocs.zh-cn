---
title: bitsadmin list
description: Bitsadmin list 命令的参考文章，其中列出了当前用户拥有的传输作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1416965e-e0e6-49cf-b1d4-b286d3cf8716
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9d9a2c86536ff0910b4e0a8bea15ec43d9371087
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926550"
---
# <a name="bitsadmin-list"></a>bitsadmin list

列出当前用户拥有的传输作业。

## <a name="syntax"></a>语法

```
bitsadmin /list [/allusers][/verbose]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| /allusers | 可选。 列出所有用户的作业。 您必须具有管理员特权才能使用此参数。 |
| /verbose | 可选。 提供有关每个作业的详细信息。 |

## <a name="examples"></a>示例

检索有关当前用户拥有的作业的信息。

```
bitsadmin /list
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
