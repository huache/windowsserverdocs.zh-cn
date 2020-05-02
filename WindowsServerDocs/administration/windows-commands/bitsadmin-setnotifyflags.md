---
title: bitsadmin setnotifyflags
description: Bitsadmin setnotifyflags 命令的参考主题，用于设置指定作业的事件通知标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 00b704bf0943790ef01bbfbdbcbbde4dfd1845c6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717273"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

设置指定作业的事件通知标志。

## <a name="syntax"></a>语法

```
bitsadmin /setnotifyflags <job> <notifyflags>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| notifyflags | 可以包含以下一个或多个通知标志，其中包括：<ul><li>**1.** 当作业中的所有文件都已传输时生成事件。</li><li>**2.** 发生错误时生成事件。</li><li>**3.** 在所有文件完成传输或发生错误时生成事件。</li><li>**4.** 禁用通知。</li></ul> |

## <a name="examples"></a>示例

若要设置通知标志以便在发生错误时生成事件，请针对名为*myDownloadJob*的作业：

```
bitsadmin /setnotifyflags myDownloadJob 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
