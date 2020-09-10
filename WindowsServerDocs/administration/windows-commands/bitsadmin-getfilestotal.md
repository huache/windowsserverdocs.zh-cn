---
title: bitsadmin getfilestotal
description: Bitsadmin getfilestotal 命令的参考文章，可检索指定作业中的文件数。
ms.topic: reference
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 73a543914f31a7b9e5b028caf273d7945a954fdd
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632099"
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
