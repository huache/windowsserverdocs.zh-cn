---
title: bitsadmin peercaching 和 getconfigurationflags
description: Bitsadmin 对等互连和 getconfigurationflags 命令的参考主题，该主题获取确定计算机是否向对等机提供内容以及是否可以从对等方下载内容的配置标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 124ddc15-3444-4bd5-96e5-c6bfabe4f9c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 62b6848dec30a9a9fef401b1b2372605dbb9934a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717322"
---
# <a name="bitsadmin-peercaching-and-getconfigurationflags"></a>bitsadmin peercaching 和 getconfigurationflags

获取用于确定计算机是否向对等方提供内容以及是否可以从对等方下载内容的配置标志。

## <a name="syntax"></a>语法

```
bitsadmin /peercaching /getconfigurationflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要获取名为*myDownloadJob*的作业的配置标志：

```
bitsadmin /peercaching /getconfigurationflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)

- [bitsadmin 对等缓存命令](bitsadmin-peercaching.md)
