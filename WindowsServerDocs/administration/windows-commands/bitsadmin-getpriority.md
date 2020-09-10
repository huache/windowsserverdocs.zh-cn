---
title: bitsadmin getpriority
description: Bitsadmin getpriority 命令的参考文章，它检索指定作业的优先级。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 397a762a210aeae7a02e49283330a2d4214876e6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631767"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin getpriority

检索指定的作业的优先级。

## <a name="syntax"></a>语法

```
bitsadmin /getpriority <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>输出

此命令的返回优先级可以是：

- **后台**

- **严重**

- **一般**

- **低级**

- UNKNOWN

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的优先级：

```
bitsadmin /getpriority myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
