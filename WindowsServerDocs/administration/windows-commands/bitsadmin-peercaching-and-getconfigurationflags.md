---
title: bitsadmin peercaching 和 getconfigurationflags
description: Bitsadmin 对等互连和 getconfigurationflags 命令的参考文章，可获取确定计算机是否向对等机提供内容以及是否可以从对等机下载内容的配置标志。
ms.topic: reference
ms.assetid: 124ddc15-3444-4bd5-96e5-c6bfabe4f9c2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3fe1adfb44ab845ecdb73222131191782f83c075
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631376"
---
# <a name="bitsadmin-peercaching-and-getconfigurationflags"></a>bitsadmin peercaching 和 getconfigurationflags

获取用于确定计算机是否向对等方提供内容以及是否可以从对等方下载内容的配置标志。

## <a name="syntax"></a>语法

```
bitsadmin /peercaching /getconfigurationflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要获取名为 *myDownloadJob*的作业的配置标志：

```
bitsadmin /peercaching /getconfigurationflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)

- [bitsadmin 对等缓存命令](bitsadmin-peercaching.md)
