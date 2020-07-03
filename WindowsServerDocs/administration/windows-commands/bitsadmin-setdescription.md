---
title: bitsadmin setdescription
description: Bitsadmin setdescription 命令的参考文章，用于设置指定作业的说明。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9c22909193667ff3222576010498d7b2fbcf14c7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927835"
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

若要检索名为*myDownloadJob*的作业的说明：

```
bitsadmin /setdescription myDownloadJob music_downloads
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
