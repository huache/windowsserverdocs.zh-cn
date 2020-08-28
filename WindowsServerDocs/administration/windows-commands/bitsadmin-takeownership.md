---
title: bitsadmin takeownership
description: Bitsadmin takeownership 命令的参考文章，可让具有管理权限的用户取得指定作业的所有权。
ms.topic: reference
ms.assetid: ea0ce7cb-440a-498f-a3ef-8368fa43e399
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b0df40e336ecc282e4b1a1774d7b5848f37a1a7a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033375"
---
# <a name="bitsadmin-takeownership"></a>bitsadmin takeownership

允许具有管理权限的用户取得指定作业的所有权。

## <a name="syntax"></a>语法

```
bitsadmin /takeownership <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ---------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

获取名为 *myDownloadJob*的作业的所有权：

```
bitsadmin /takeownership myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
