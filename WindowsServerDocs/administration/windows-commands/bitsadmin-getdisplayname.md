---
title: bitsadmin getdisplayname
description: Bitsadmin getdisplayname 命令的参考文章，可检索指定作业的显示名称。
ms.topic: article
ms.assetid: e5c0e76c-4cc6-42d8-ac30-30bf3dc11b9b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8ddc6e2f73062abca7c711a02c9c3a4f9c725bde
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894387"
---
# <a name="bitsadmin-getdisplayname"></a>bitsadmin getdisplayname

检索指定作业的显示名称。

## <a name="syntax"></a>语法

```
bitsadmin /getdisplayname <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的显示名称，请执行以下操作：

```
bitsadmin /getdisplayname myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
