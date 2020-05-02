---
title: bitsadmin gettemporaryname
description: Bitsadmin gettemporaryname 命令的参考主题，它报告作业中给定文件的临时文件名。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 68925edc-a801-4292-a812-7471c4f60fdd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f7780691f37fb78f1553fa993fd408d224be39ff
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717486"
---
# <a name="bitsadmin-gettemporaryname"></a>bitsadmin gettemporaryname

报告作业中给定文件的临时文件名。

## <a name="syntax"></a>语法

```
bitsadmin /gettemporaryname <job> <file_index>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| file_index | 从0开始。 |

## <a name="examples"></a>示例

若要报告名为*myDownloadJob*的作业的文件2的临时文件名，请执行以下操作：

```
bitsadmin /gettemporaryname myDownloadJob 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
