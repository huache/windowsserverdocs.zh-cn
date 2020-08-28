---
title: bitsadmin getfilestotal
description: Bitsadmin getfilestotal 命令的参考文章，可检索指定作业中的文件数。
ms.topic: reference
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 74e5dad863b12b7f90ed74bca0e6b0b352fb1360
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033605"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal

检索指定的作业中的文件数。

## <a name="syntax"></a>语法

```
bitsadmin /getfilestotal <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索包含在名为 *myDownloadJob*的作业中的文件数：

```
bitsadmin /getfilestotal myDownloadJob
```

## <a name="see-also"></a>另请参阅

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
