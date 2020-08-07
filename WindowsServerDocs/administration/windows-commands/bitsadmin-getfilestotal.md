---
title: bitsadmin getfilestotal
description: Bitsadmin getfilestotal 命令的参考文章，可检索指定作业中的文件数。
ms.topic: article
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 09867e5ed8b060f7a9cbfe573c6e98bfbac831df
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894340"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal

检索指定的作业中的文件数。

## <a name="syntax"></a>语法

```
bitsadmin /getfilestotal <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
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
