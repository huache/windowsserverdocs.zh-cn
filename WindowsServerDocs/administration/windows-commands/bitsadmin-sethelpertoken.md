---
title: bitsadmin sethelpertoken
description: Bitsadmin sethelpertoken 命令的参考文章，如果指定) 作为 BITS 传输作业的帮助程序令牌，则该命令将 (或任意本地用户帐户的令牌设置为当前命令提示符的主要令牌。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: a691d010aa112f1ac609077be6a6968f79d73c72
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630918"
---
# <a name="bitsadmin-sethelpertoken"></a>bitsadmin sethelpertoken

如果) 指定为 BITS 传输作业的 [帮助程序令牌](/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)，则将当前命令提示符的主令牌 (或任意本地用户帐户的令牌。

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
