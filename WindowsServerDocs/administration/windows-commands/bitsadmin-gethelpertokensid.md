---
title: bitsadmin gethelpertokensid
description: 适用于**bitsadmin gethelpertokensid**的 Windows 命令主题，返回 BITS 传输作业的帮助程序令牌的 SID （如果已设置）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: a2e26ff459b068595529fbd24e6165c130660570
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850640"
---
# <a name="bitsadmin-gethelpertokensid"></a>bitsadmin gethelpertokensid

返回 BITS 传输作业的 [帮助程序令牌](https://docs.microsoft.com/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)的 SID （如果已设置）。

> [!NOTE]
> BITS 3.0 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /gethelpertokensid <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
