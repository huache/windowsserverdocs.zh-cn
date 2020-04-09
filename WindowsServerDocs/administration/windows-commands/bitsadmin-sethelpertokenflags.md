---
title: bitsadmin sethelpertokenflags
description: 适用于 bitsadmin sethelpertokenflags 的 Windows 命令主题，用于设置与 BITS 传输作业关联的帮助程序令牌的使用标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: c644e82026cfc1d62f3fb5d20e3925002b871036
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849490"
---
# <a name="bitsadmin-sethelpertokenflags"></a>bitsadmin sethelpertokenflags

为与 BITS 传输作业关联 的 [帮助程序令牌](/windows/desktop/bits/helper-tokens-for-bits-transfer-jobs)设置使用标志。

**BITS 3.0 及更早版本**：不支持。

## <a name="syntax"></a>语法

```
bitsadmin /SetHelperTokenFlags <Job> <Flags>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|作业的显示名称或 GUID。|
|Flags|可能的值包括以下各项。 0x0001&mdash;帮助程序令牌用于打开上传作业的本地文件，创建或重命名下载作业的临时文件，或创建或重命名上传答复作业的答复文件。 0x0002&mdash;帮助程序令牌用于打开服务器消息块（SMB）上传或下载作业的远程文件，或响应隐式 NTLM 或 Kerberos 凭据的 HTTP 服务器或代理质询。 必须调用 `/SetCredentialsJob TargetScheme NULL NULL` ，以允许通过 HTTP 发送凭据。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
