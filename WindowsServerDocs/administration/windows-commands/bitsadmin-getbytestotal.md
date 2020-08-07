---
title: bitsadmin getbytestotal
description: 用于检索指定作业大小的 bitsadmin getbytestotal 命令的参考文章。
ms.topic: article
ms.assetid: 784e0bfa-7b09-4262-9104-adbc9beb479b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b26773578d4c9a24f969df1506828c202e12b41
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894568"
---
# <a name="bitsadmin-getbytestotal"></a>bitsadmin getbytestotal

检索指定作业的大小。

## <a name="syntax"></a>语法

```
bitsadmin /getbytestotal <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的大小：

```
bitsadmin /getbytestotal myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
