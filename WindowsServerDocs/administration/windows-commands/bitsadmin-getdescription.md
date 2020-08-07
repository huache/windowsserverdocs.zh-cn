---
title: bitsadmin getdescription
description: Bitsadmin getdescription 命令的参考文章，可检索指定作业的说明。
ms.topic: article
ms.assetid: f3974603-ebbe-4d31-8217-040fe2d90c85
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e5023a0a4114796fa3a492de4fddaa0d5ddb0187
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894403"
---
# <a name="bitsadmin-getdescription"></a>bitsadmin getdescription

检索指定作业的说明。

## <a name="syntax"></a>语法

```
bitsadmin /getdescription <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的说明：

```
bitsadmin /getdescription myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
