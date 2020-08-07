---
title: bitsadmin complete
description: Bitsadmin complete 命令的参考文章，用于完成作业。
ms.topic: article
ms.assetid: a5e86677-8f7b-43b3-929e-97706c57e7f1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 43c3296520b5843643c10d204d89f4f2f2bf98d8
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894610"
---
# <a name="bitsadmin-complete"></a>bitsadmin complete

完成作业。 作业转到已转移的状态后，请使用此开关。 否则，只会提供已成功传输的文件。

## <a name="syntax"></a>语法

```
bitsadmin /complete <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="example"></a>示例

若要完成*myDownloadJob*作业，请在达到 `TRANSFERRED` 以下状态后：

```
bitsadmin /complete myDownloadJob
```

如果有多个作业使用*myDownloadJob*作为其名称，则必须使用作业的 GUID 来唯一地标识该作业才能完成。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
