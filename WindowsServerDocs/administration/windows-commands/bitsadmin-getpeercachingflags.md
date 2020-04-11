---
title: bitsadmin getpeercachingflags
description: 适用于**bitsadmin getpeercachingflags**的 Windows 命令主题，它检索确定是否可以缓存作业的文件并将其提供给对等方的标志，以及 BITS 是否可以从对等方下载作业的内容。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3c3c9f28-4c04-4c49-a23a-dee5bbcc8981
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 59ff3e3a5802c6023d85129c82f19cd7ee625d2f
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123124"
---
# <a name="bitsadmin-getpeercachingflags"></a>bitsadmin getpeercachingflags

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

检索标志，该标志确定是否可以缓存作业的文件并将其提供给对等方，以及 BITS 是否可以从对等方下载作业的内容。

## <a name="syntax"></a>语法

```
bitsadmin /getpeercachingflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为*myDownloadJob*的作业的标志。

```
C:\>bitsadmin /getpeercachingflags myJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)