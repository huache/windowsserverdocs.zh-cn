---
title: bitsadmin getowner
description: 用于检索指定作业的所有者的 bitsadmin getowner 命令的参考文章。
ms.topic: reference
ms.assetid: 5203f84c-a879-4f31-ae3e-7ea74bd63ca5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2839936113e304e9c57308042f5c8cf66e887d36
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631869"
---
# <a name="bitsadmin-getowner"></a>bitsadmin getowner

显示指定作业的所有者的显示名称或 GUID。

## <a name="syntax"></a>语法

```
bitsadmin /getowner <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要显示名为 *myDownloadJob*的作业的所有者：

```
bitsadmin /getowner myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
