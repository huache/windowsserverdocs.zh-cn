---
title: bitsadmin getproxylist-检索指定作业的代理列表。
description: Bitsadmin getproxylist 命令的参考文章，它检索指定作业的代理列表。
ms.topic: reference
ms.assetid: eebfa727-d8f1-4ae3-9382-6d8ffe8c3df3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4d4cefcb27a9aa18b06bc588d08aba2f2f810636
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631740"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

检索要用于指定作业的代理服务器的逗号分隔列表。

## <a name="syntax"></a>语法

```
bitsadmin /getproxylist <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的代理列表：

```
bitsadmin /getproxylist myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
