---
title: bitsadmin gethttpmethod
description: Bitsadmin gethttpmethod 命令的参考文章，用于获取用于作业的 HTTP 谓词。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 0d96c85aa99330b133954a77ca5584fe2d02cd43
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632032"
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
