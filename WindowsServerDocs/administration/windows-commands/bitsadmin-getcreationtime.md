---
title: bitsadmin getcreationtime
description: Bitsadmin getcreationtime 命令的参考文章，它检索指定作业的创建时间。
ms.topic: reference
ms.assetid: be409cb5-ce72-41d9-aafa-edd4e230fd14
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 780f7124248bd38f0c3d7cc9e7cb14b1a9decc03
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632237"
---
# <a name="bitsadmin-getcreationtime"></a>bitsadmin getcreationtime

检索指定作业的创建时间。

## <a name="syntax"></a>语法

```
bitsadmin /getcreationtime <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的创建时间：

```
bitsadmin /getcreationtime myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
