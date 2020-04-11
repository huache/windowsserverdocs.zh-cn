---
title: bitsadmin setpeercachingflags
description: 适用于**bitsadmin setpeercachingflags**的 Windows 命令主题，用于设置标志，这些标志确定是否可以缓存作业的文件并将其提供给对等方以及作业是否可以从对等方下载内容。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3f54a127-fb68-49a5-b843-664ec833df67
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1b4a7807975fb46440301e30b1fdbd01784d7c85
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122779"
---
# <a name="bitsadmin-setpeercachingflags"></a>bitsadmin setpeercachingflags

设置标志，该标志确定是否可以缓存作业的文件并将其提供给对等方以及作业是否可以从对等方下载内容。

## <a name="syntax"></a>语法

```
bitsadmin /setpeercachingflags <job> <value>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| 值 | 无符号整数，其中包括：<ul><li>**1.** 作业可以从对等方下载内容。</li><li>**2.** 该作业的文件可以缓存并提供给对等方。</li></ul> |

## <a name="examples"></a>示例

下面的示例设置名为*myDownloadJob*的作业的标志，使其能够从对等方下载内容。

```
C:\>bitsadmin /setpeercachingflags myDownloadJob 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)