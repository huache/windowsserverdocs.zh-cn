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
ms.openlocfilehash: 21dee45610823cd70e8b7209ec99e080746316f9
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927784"
---
# <a name="bitsadmin-sethelpertoken"></a>bitsadmin sethelpertoken

将当前命令提示符的主要令牌（或任意本地用户帐户的令牌，如果指定）设置为 BITS 传输作业的 [帮助令牌](https://docs.microsoft.com/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)。

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
