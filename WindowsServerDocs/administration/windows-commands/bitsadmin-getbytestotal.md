---
title: bitsadmin getbytestotal
description: 用于检索指定作业大小的 bitsadmin getbytestotal 命令的参考文章。
ms.topic: reference
ms.assetid: 784e0bfa-7b09-4262-9104-adbc9beb479b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 50b926b8d89e402ef4fd9e58896963edd3c368c9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632341"
---
# <a name="bitsadmin-getbytestotal"></a>bitsadmin getbytestotal

检索指定作业的大小。

## <a name="syntax"></a>语法

```
bitsadmin /getbytestotal <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的大小：

```
bitsadmin /getbytestotal myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
