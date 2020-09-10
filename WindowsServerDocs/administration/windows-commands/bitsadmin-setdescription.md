---
title: bitsadmin setdescription
description: Bitsadmin setdescription 命令的参考文章，用于设置指定作业的说明。
ms.topic: reference
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a306605d447a3bc3a40b16f75a1a63badf75f3b0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630944"
---
# <a name="bitsadmin-setdescription"></a>bitsadmin setdescription

设置指定作业的说明。

## <a name="syntax"></a>语法

```
bitsadmin /setdescription <job> <description>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| description | 用于描述作业的文本。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的说明：

```
bitsadmin /setdescription myDownloadJob music_downloads
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
