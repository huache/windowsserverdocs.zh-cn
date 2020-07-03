---
title: bitsadmin takeownership
description: Bitsadmin takeownership 命令的参考文章，可让具有管理权限的用户取得指定作业的所有权。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ea0ce7cb-440a-498f-a3ef-8368fa43e399
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc406d1d5f7c9553082f85f3315ab7622f6bc7db
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927465"
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

获取名为*myDownloadJob*的作业的所有权：

```
bitsadmin /takeownership myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
