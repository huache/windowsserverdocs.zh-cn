---
title: bitsadmin setnotifyflags
description: 用于为指定作业设置事件通知标志的 bitsadmin setnotifyflags 命令的参考文章。
ms.topic: reference
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 48eb165ecb32e53868f9636418437d66c56542c0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630777"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

设置指定作业的事件通知标志。

## <a name="syntax"></a>语法

```
bitsadmin /setnotifyflags <job> <notifyflags>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| notifyflags | 可以包含以下一个或多个通知标志，其中包括：<ul><li>**1.** 当作业中的所有文件都已传输时生成事件。</li><li>**2.** 发生错误时生成事件。</li><li>**3.** 在所有文件完成传输或发生错误时生成事件。</li><li>**4.** 禁用通知。</li></ul> |

## <a name="examples"></a>示例

若要设置通知标志以便在发生错误时生成事件，请针对名为 *myDownloadJob*的作业：

```
bitsadmin /setnotifyflags myDownloadJob 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
