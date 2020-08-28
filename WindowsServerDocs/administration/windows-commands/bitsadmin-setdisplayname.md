---
title: bitsadmin setdisplayname
description: Bitsadmin setdisplayname 命令的参考文章，用于设置指定作业的显示名称。
ms.topic: reference
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4726d4d1dec867e72ab542222a71289994ed12fd
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028535"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname

设置指定作业的显示名称。

## <a name="syntax"></a>语法

```
bitsadmin /setdisplayname <job> <display_name>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| display_name | 用作特定作业的显示名称的文本。 |

## <a name="examples"></a>示例

将作业的显示名称设置为 *myDownloadJob*：

```
bitsadmin /setdisplayname myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
