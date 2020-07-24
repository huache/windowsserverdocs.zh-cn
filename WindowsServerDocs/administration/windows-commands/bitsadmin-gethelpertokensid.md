---
title: bitsadmin gethelpertokensid
description: Bitsadmin gethelpertokensid 命令的参考文章，返回 BITS 传输作业的帮助程序令牌的 SID （如果已设置）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 3c8ef7502c524994454c697e2fa7d5dee223da5d
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86955459"
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

若要检索名为*myDownloadJob*的 BITS 传输作业的 SID：

```
bitsadmin /gethelpertokensid myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
