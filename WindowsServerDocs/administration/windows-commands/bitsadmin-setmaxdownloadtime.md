---
title: bitsadmin setmaxdownloadtime
description: Bitsadmin setmaxdownloadtime 命令的参考文章，用于设置下载超时（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 16b96cf1-5738-415c-9b9d-c4ea8d5e4fec
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 65853180a22d49011e8edb10ed15ac98625cbc30
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927738"
---
# <a name="bitsadmin-setmaxdownloadtime"></a>bitsadmin setmaxdownloadtime

设置下载超时（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /setmaxdownloadtime <job> <timeout>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| timeout | 下载超时的长度（以秒为单位）。 |

## <a name="examples"></a>示例

将名为*myDownloadJob*的作业的超时值设置为10秒。

```
bitsadmin /setmaxdownloadtime myDownloadJob 10
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
