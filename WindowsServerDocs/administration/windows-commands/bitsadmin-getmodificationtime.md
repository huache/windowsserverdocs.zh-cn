---
title: bitsadmin getmodificationtime
description: Bitsadmin getmodificationtime 命令的参考文章，用于检索上次修改作业或成功传输数据的时间。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e543945e-92c4-491e-8c2d-344f8a3e342d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9055c0ac70bc2360601ecd1b1f91c8ad3908d704
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85928167"
---
# <a name="bitsadmin-getmodificationtime"></a>bitsadmin getmodificationtime

已成功传送检索上次修改作业的时间或数据。

## <a name="syntax"></a>语法

```
bitsadmin /getmodificationtime <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的上次修改时间：

```
bitsadmin /getmodificationtime myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
