---
title: bitsadmin getpeercachingflags
description: Bitsadmin getpeercachingflags 命令的参考文章，它检索确定是否可以缓存作业的文件并为对等方提供服务的标志，以及 BITS 能否从对等方下载作业的内容。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3c3c9f28-4c04-4c49-a23a-dee5bbcc8981
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ad270fb8003c518c43bae86b066fea5ebc31d008
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926865"
---
# <a name="bitsadmin-getpeercachingflags"></a>bitsadmin getpeercachingflags

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

检索标志，该标志确定是否可以缓存作业的文件并将其提供给对等方，以及 BITS 是否可以从对等方下载作业的内容。

## <a name="syntax"></a>语法

```
bitsadmin /getpeercachingflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的标志：

```
bitsadmin /getpeercachingflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
