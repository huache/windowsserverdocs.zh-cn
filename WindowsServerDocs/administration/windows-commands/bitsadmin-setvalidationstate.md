---
title: bitsadmin setvalidationstate
description: Bitsadmin setvalidationstate 命令的参考文章，用于设置作业中给定文件的内容验证状态。
ms.topic: reference
ms.assetid: e8fc8e8c-171c-4681-8057-6986b018e576
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5885f0f43e7c33e55dc05182819a339d69519d84
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034725"
---
# <a name="bitsadmin-setvalidationstate"></a>bitsadmin setvalidationstate

设置作业中给定文件的内容验证状态。

## <a name="syntax"></a>语法

```
bitsadmin /setvalidationstate <job> <file_index> <TRUE|FALSE>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ---------- |
| 作业 | 作业的显示名称或 GUID。 |
| file_index | 从0开始。 |
| TRUE 或 FALSE | **如果为 TRUE，则** 为指定文件启用内容验证，而 **FALSE** 则禁用。 |

## <a name="examples"></a>示例

若要将名为 *myDownloadJob*的作业的文件2的内容验证状态设置为 TRUE：

```
bitsadmin /setvalidationstate myDownloadJob 2 TRUE
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
