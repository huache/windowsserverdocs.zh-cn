---
title: bitsadmin info
description: Bitsadmin info 命令的参考文章，其中显示有关指定作业的摘要信息。
ms.topic: reference
ms.assetid: 5c306677-0d64-41c0-8276-5bba7750cecb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 815fdc719d584f7d25f88705056e4d5c0c3405aa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631545"
---
# <a name="bitsadmin-info"></a>bitsadmin info

显示有关指定作业的摘要信息。

## <a name="syntax"></a>语法

```
bitsadmin /info <job> [/verbose]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| /verbose | 可选。 提供有关每个作业的详细信息。 |

## <a name="examples"></a>示例

若要检索有关名为 *myDownloadJob*的作业的信息：

```
bitsadmin /info myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin info](bitsadmin-info.md)
