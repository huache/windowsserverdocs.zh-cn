---
title: bitsadmin getpriority
description: Bitsadmin getpriority 命令的参考文章，它检索指定作业的优先级。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 39ce769e2eb1dcf7a05d416dc2a66c6c082c9ae4
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926854"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin getpriority

检索指定的作业的优先级。

## <a name="syntax"></a>语法

```
bitsadmin /getpriority <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>输出

此命令的返回优先级可以是：

- **后台**

- **严重**

- **一般**

- **低级**

- **未知**

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的优先级：

```
bitsadmin /getpriority myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
