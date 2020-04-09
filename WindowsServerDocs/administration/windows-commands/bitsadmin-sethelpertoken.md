---
title: bitsadmin sethelpertoken
description: 适用于 bitsadmin sethelpertoken 的 Windows 命令主题，它将当前命令提示符的主要令牌（或任意本地用户帐户的令牌，如果指定）设置为 BITS 传输作业的帮助令牌。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: a1e8fd0054cadf3bf06b6e5b7bdf5010b18781e1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849530"
---
# <a name="bitsadmin-sethelpertoken"></a>bitsadmin sethelpertoken

将当前命令提示符的主要令牌（或任意本地用户帐户的令牌，如果指定）设置为 BITS 传输作业的 [帮助令牌](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs)。

**BITS 3.0 及更早版本**：不支持。

## <a name="syntax"></a>语法

```
bitsadmin /SetHelperToken <Job> [\<username@domain\> \<password\>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|作业的显示名称或 GUID。|
|\<username@domain\> \<密码\>|可选&mdash;要使用其令牌的本地用户帐户的凭据。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
