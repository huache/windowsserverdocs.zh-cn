---
title: bitsadmin makecustomheaderswriteonly
description: Bitsadmin makecustomheaderswriteonly 命令的参考文章，可将作业的自定义 HTTP 标头设置为只写。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 4d31f51c2531079342e223752c626b0b7e8d19f8
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024261"
---
# <a name="bitsadmin-makecustomheaderswriteonly"></a>bitsadmin makecustomheaderswriteonly

将作业的自定义 HTTP 标头设置为只写。

> [!IMPORTANT]
> 此操作无法撤消。

## <a name="syntax"></a>语法

```
bitsadmin /makecustomheaderswriteonly <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要为名为 *myDownloadJob*的作业仅编写自定义 HTTP 标头：

```
bitsadmin /makecustomheaderswriteonly myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
