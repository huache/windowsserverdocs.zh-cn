---
title: bitsadmin setpriority
description: Bitsadmin setpriority 命令的参考文章，用于设置指定作业的优先级。
ms.topic: article
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1326d4d5eb8a488dde542c33fa886482e753a790
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87892989"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority

设置指定作业的优先级。

## <a name="syntax"></a>语法

```
bitsadmin /setpriority <job> <priority>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| priority | 设置作业的优先级，包括：<ul><li>FOREGROUND</li><li>HIGH</li><li>NORMAL</li><li>LOW</li></ul> |

## <a name="examples"></a>示例

若要将名为*myDownloadJob*的作业的优先级设置为 normal：

```
bitsadmin /setpriority myDownloadJob NORMAL
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
