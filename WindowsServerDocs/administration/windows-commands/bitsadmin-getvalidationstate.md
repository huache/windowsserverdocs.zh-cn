---
title: bitsadmin getvalidationstate
description: Bitsadmin getvalidationstate 命令的参考文章，它报告作业中给定文件的内容验证状态。
ms.topic: reference
ms.assetid: 6ada3f1f-9967-4262-9d22-ed641e23f516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 173bbaad6508ec3ae8100232fda598fe7a422296
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028635"
---
# <a name="bitsadmin-getvalidationstate"></a>bitsadmin getvalidationstate

报告作业中给定文件的内容验证状态。

## <a name="syntax"></a>语法

```
bitsadmin /getvalidationstate <job> <file_index>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| file_index | 从0开始。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业中的文件2的内容验证状态，请执行以下操作：

```
bitsadmin /getvalidationstate myDownloadJob 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
