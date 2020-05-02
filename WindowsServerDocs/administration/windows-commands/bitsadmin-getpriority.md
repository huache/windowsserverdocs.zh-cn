---
title: bitsadmin getpriority
description: Bitsadmin getpriority 命令的参考主题，它检索指定作业的优先级。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 38f92e83ccf5b048d168ce6a21c6026f490b18bf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717678"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin getpriority

检索指定的作业的优先级。

## <a name="syntax"></a>语法

```
bitsadmin /getpriority <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
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
