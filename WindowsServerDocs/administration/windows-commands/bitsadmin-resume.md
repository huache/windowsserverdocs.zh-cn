---
title: bitsadmin resume
description: Bitsadmin resume 命令的参考文章，用于激活传输队列中的新作业或挂起的作业。
ms.topic: article
ms.assetid: 7c7540a9-a11a-4910-923a-2a2a61cbf11d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a18bd6c0a69ff4b366f66d34ec472be9aaeecba2
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893307"
---
# <a name="bitsadmin-resume"></a>bitsadmin resume

激活传输队列中的新作业或挂起的作业。 如果错误地恢复了作业，或者只是需要暂停作业，则可以使用[bitsadmin 挂起](bitsadmin-suspend.md)开关来暂停作业。

## <a name="syntax"></a>语法

```
bitsadmin /resume <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要恢复名为*myDownloadJob*的作业：

```
bitsadmin /resume myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 挂起命令](bitsadmin-suspend.md)

- [bitsadmin 命令](bitsadmin.md)
