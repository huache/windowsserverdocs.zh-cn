---
title: bitsadmin getdescription
description: Bitsadmin getdescription 命令的参考文章，可检索指定作业的说明。
ms.topic: reference
ms.assetid: f3974603-ebbe-4d31-8217-040fe2d90c85
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c8233ab420cadf3e7f578ce6f38d7631a8a1e820
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030415"
---
# <a name="bitsadmin-getdescription"></a>bitsadmin getdescription

检索指定作业的说明。

## <a name="syntax"></a>语法

```
bitsadmin /getdescription <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的说明：

```
bitsadmin /getdescription myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
