---
title: bitsadmin takeownership
description: Bitsadmin takeownership 命令的参考主题，该主题允许具有管理权限的用户取得指定作业的所有权。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ea0ce7cb-440a-498f-a3ef-8368fa43e399
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5369cb3fa143ebde77ae8cabf04b9a38eed5b9c5
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720444"
---
# <a name="bitsadmin-takeownership"></a>bitsadmin takeownership

允许具有管理权限的用户取得指定作业的所有权。

## <a name="syntax"></a>语法

```
bitsadmin /takeownership <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
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
