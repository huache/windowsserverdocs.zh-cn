---
title: bitsadmin setpriority
description: Bitsadmin setpriority 命令的参考文章，用于设置指定作业的优先级。
ms.topic: reference
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b1fe6a2b3981697a4a8c287fe4fb49c31a4f4244
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028465"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority

设置指定作业的优先级。

## <a name="syntax"></a>语法

```
bitsadmin /setpriority <job> <priority>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| priority | 设置作业的优先级，包括：<ul><li>FOREGROUND</li><li>HIGH</li><li>NORMAL</li><li>LOW</li></ul> |

## <a name="examples"></a>示例

若要将名为 *myDownloadJob* 的作业的优先级设置为 normal：

```
bitsadmin /setpriority myDownloadJob NORMAL
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
