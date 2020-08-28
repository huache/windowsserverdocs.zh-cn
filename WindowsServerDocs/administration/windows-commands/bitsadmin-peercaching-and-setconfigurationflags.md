---
title: bitsadmin peercaching 和 setconfigurationflags
description: Bitsadmin 对等互连和 setconfigurationflags 命令的参考文章，设置用于确定计算机能否向对等机提供内容以及是否可以从对等机下载内容的配置标志。
ms.topic: reference
ms.assetid: ff0a2b49-66e3-4d40-824c-6a3816055d2e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0027fa5c926f09b95541906f168e852292b19aaf
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026516"
---
# <a name="bitsadmin-peercaching-and-setconfigurationflags"></a>bitsadmin peercaching 和 setconfigurationflags

设置配置标志，这些标志确定计算机是否可以向对等方提供内容以及是否可以从对等方下载内容。

## <a name="syntax"></a>语法

```
bitsadmin /peercaching /setconfigurationflags <job> <value>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| value | 一个无符号整数，其中的二进制表示形式中的位解释如下：<ul><li>若要允许从对等机下载作业的数据，请设置最小有效位。</li><li>若要允许将作业的数据提供给对等节点，请设置第二个位。</li></ul>|

## <a name="examples"></a>示例

若要为名为 *myDownloadJob*的作业指定要从对等机下载的作业数据：

```
bitsadmin /peercaching /setconfigurationflags myDownloadJob 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)

- [bitsadmin 对等缓存命令](bitsadmin-peercaching.md)
