---
title: bitsadmin setdisplayname
description: Bitsadmin setdisplayname 命令的参考文章，用于设置指定作业的显示名称。
ms.topic: article
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ac83fee33703555f1a8ba4b65ae8dc4d0f947916
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893169"
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
