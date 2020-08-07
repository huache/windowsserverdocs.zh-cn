---
title: bitsadmin getproxylist-检索指定作业的代理列表。
description: Bitsadmin getproxylist 命令的参考文章，它检索指定作业的代理列表。
ms.topic: article
ms.assetid: eebfa727-d8f1-4ae3-9382-6d8ffe8c3df3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bcd94c65a11006a795f071224397d8b3081b7548
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893974"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

检索要用于指定作业的代理服务器的逗号分隔列表。

## <a name="syntax"></a>语法

```
bitsadmin /getproxylist <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的代理列表：

```
bitsadmin /getproxylist myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
