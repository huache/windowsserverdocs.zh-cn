---
title: bitsadmin sethelpertoken
description: Bitsadmin sethelpertoken 命令的参考文章，可将当前命令提示符的主要令牌（或任意本地用户帐户的令牌，如果指定）设置为 BITS 传输作业的帮助令牌。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: e9fe469b8ae4a8a553245b1e22d48ee2cacf23e3
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86955699"
---
# <a name="bitsadmin-sethelpertoken"></a>bitsadmin sethelpertoken

将当前命令提示符的主要令牌（或任意本地用户帐户的令牌，如果指定）设置为 BITS 传输作业的 [帮助令牌](/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)。

> [!NOTE]
> BITS 3.0 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /sethelpertoken <job> [<user_name@domain> <password>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| `<username@domain>` `<password>` | 可选。 要使用令牌的本地用户帐户凭据。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
