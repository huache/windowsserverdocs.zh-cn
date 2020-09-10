---
title: bitsadmin setdisplayname
description: Bitsadmin setdisplayname 命令的参考文章，用于设置指定作业的显示名称。
ms.topic: reference
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 57a72d198b7d262f3a7958920e5d54955f8b6270
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630929"
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
