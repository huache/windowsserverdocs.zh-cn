---
title: bitsadmin gettemporaryname
description: Bitsadmin gettemporaryname 命令的参考文章，用于报告作业中给定文件的临时文件名。
ms.topic: reference
ms.assetid: 68925edc-a801-4292-a812-7471c4f60fdd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d9e03b00fa1885b89f25dab2781ce988aa0c5df8
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034805"
---
# <a name="bitsadmin-gettemporaryname"></a>bitsadmin gettemporaryname

报告作业中给定文件的临时文件名。

## <a name="syntax"></a>语法

```
bitsadmin /gettemporaryname <job> <file_index>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| file_index | 从0开始。 |

## <a name="examples"></a>示例

若要报告名为 *myDownloadJob*的作业的文件2的临时文件名，请执行以下操作：

```
bitsadmin /gettemporaryname myDownloadJob 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
