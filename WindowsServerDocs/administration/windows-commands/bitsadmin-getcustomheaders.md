---
title: bitsadmin getcustomheaders
description: Bitsadmin getcustomheaders 命令的参考文章，用于从作业中检索自定义 HTTP 标头。
ms.topic: article
ms.assetid: 1f0d38d3-e865-4474-81e8-773d65c3d1cc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3cc970a7aeee1be678a3c77d852af91ae0ab98c8
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894416"
---
# <a name="bitsadmin-getcustomheaders"></a>bitsadmin getcustomheaders

从作业检索自定义 HTTP 标头。

## <a name="syntax"></a>语法

```
bitsadmin /getcustomheaders <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要获取名为*myDownloadJob*的作业的自定义标头：

```
bitsadmin /getcustomheaders myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
