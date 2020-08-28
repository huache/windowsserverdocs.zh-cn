---
title: bitsadmin getdisplayname
description: Bitsadmin getdisplayname 命令的参考文章，可检索指定作业的显示名称。
ms.topic: reference
ms.assetid: e5c0e76c-4cc6-42d8-ac30-30bf3dc11b9b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bb953125ade98ecc158d61e53ea7f4462c455b15
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030389"
---
# <a name="bitsadmin-getdisplayname"></a>bitsadmin getdisplayname

检索指定作业的显示名称。

## <a name="syntax"></a>语法

```
bitsadmin /getdisplayname <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的显示名称，请执行以下操作：

```
bitsadmin /getdisplayname myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
