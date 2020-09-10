---
title: bitsadmin geterrorcount
description: Bitsadmin geterrorcount 命令的参考文章，它检索指定作业产生暂时性错误的次数的计数。
ms.topic: reference
ms.assetid: 8840ae78-52b0-4c7e-b592-0547359a237e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7266af9244218cf4a6434c838390eac8149c80ab
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632118"
---
# <a name="bitsadmin-geterrorcount"></a>bitsadmin geterrorcount

检索指定的作业生成的暂时性错误的次数计数。

## <a name="syntax"></a>语法

```
bitsadmin /geterrorcount <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的错误计数信息：

```
bitsadmin /geterrorcount myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
