---
title: bitsadmin listfiles
description: Bitsadmin listfiles 命令的参考文章，其中列出了指定作业中的文件。
ms.topic: reference
ms.assetid: ad0d1eaa-3bd8-45e5-8f72-4da7366f0d59
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 702c2d3d3370275373a91aef63aa82f7e84bcf14
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631512"
---
# <a name="bitsadmin-listfiles"></a>bitsadmin listfiles

列出指定作业中的文件。

## <a name="syntax"></a>语法

```
bitsadmin /listfiles <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的文件列表，请执行以下操作：

```
bitsadmin /listfiles myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
