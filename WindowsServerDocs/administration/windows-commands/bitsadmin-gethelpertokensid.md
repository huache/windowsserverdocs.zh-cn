---
title: bitsadmin gethelpertokensid
description: Bitsadmin gethelpertokensid 命令的参考文章，返回 BITS 传输作业的帮助程序令牌的 SID （如果已设置）。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 645957ab5526c98e806a4e7875e1baece3d375b3
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632044"
---
# <a name="bitsadmin-gethelpertokensid"></a>bitsadmin gethelpertokensid

返回 BITS 传输作业的 [帮助程序令牌](/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)的 SID （如果已设置）。

> [!NOTE]
> BITS 3.0 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /gethelpertokensid <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的 BITS 传输作业的 SID：

```
bitsadmin /gethelpertokensid myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
