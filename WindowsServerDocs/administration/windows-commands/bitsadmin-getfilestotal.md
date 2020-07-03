---
title: bitsadmin getfilestotal
description: Bitsadmin getfilestotal 命令的参考文章，可检索指定作业中的文件数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7592f783d17e31fe8a1e7fbf82cb41e20171c9fd
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928287"
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

若要检索包含在名为*myDownloadJob*的作业中的文件数：

```
bitsadmin /getfilestotal myDownloadJob
```

## <a name="see-also"></a>另请参阅

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
