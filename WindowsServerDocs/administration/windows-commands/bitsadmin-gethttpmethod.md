---
title: bitsadmin gethttpmethod
description: Bitsadmin gethttpmethod 命令的参考文章，用于获取用于作业的 HTTP 谓词。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 5bbd2509cabea7ae68240a31cee78d9ffd3ac5e0
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033525"
---
# <a name="bitsadmin-gethttpmethod"></a>bitsadmin gethttpmethod

获取要用于作业的 HTTP 谓词。

## <a name="syntax"></a>语法

```
bitsadmin /gethttpmethod <Job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索用于名为 *myDownloadJob*的作业的 HTTP 谓词：

```
bitsadmin /gethttpmethod myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
