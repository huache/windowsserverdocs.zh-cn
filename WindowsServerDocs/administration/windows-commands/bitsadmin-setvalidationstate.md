---
title: bitsadmin setvalidationstate
description: Bitsadmin setvalidationstate 命令的参考文章，用于设置作业中给定文件的内容验证状态。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e8fc8e8c-171c-4681-8057-6986b018e576
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ae776279b742e3af5af3cf555765007bbf0eb8de
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927493"
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
| TRUE 或 FALSE | **如果为 TRUE，则**为指定文件启用内容验证，而**FALSE**则禁用。 |

## <a name="examples"></a>示例

若要将名为*myDownloadJob*的作业的文件2的内容验证状态设置为 TRUE：

```
bitsadmin /setvalidationstate myDownloadJob 2 TRUE
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
