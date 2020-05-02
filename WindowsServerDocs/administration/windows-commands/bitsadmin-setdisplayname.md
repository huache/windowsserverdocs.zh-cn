---
title: bitsadmin setdisplayname
description: Bitsadmin setdisplayname 命令的参考主题，用于设置指定作业的显示名称。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 382cb2f20f0374c2d2787c4c3d88670b4f7260cd
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719391"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname

设置指定作业的显示名称。

## <a name="syntax"></a>语法

```
bitsadmin /setdisplayname <job> <display_name>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| display_name | 用作特定作业的显示名称的文本。 |

## <a name="examples"></a>示例

将作业的显示名称设置为*myDownloadJob*：

```
bitsadmin /setdisplayname myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
