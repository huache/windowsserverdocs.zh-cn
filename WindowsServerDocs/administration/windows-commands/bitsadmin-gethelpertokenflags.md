---
title: bitsadmin gethelpertokenflags
description: 适用于**bitsadmin gethelpertokenflags**的 Windows 命令主题，它返回与 BITS 传输作业关联的帮助程序令牌的用法标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 37e40ea1f71795e0c975988169577deb205c3335
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850660"
---
# <a name="bitsadmin-gethelpertokenflags"></a>bitsadmin gethelpertokenflags

返回与 BITS 传输作业关联 的 [帮助程序令牌](https://docs.microsoft.com/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)的使用标志。

> [!NOTE]
> BITS 3.0 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /gethelpertokenflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="remarks"></a>备注

可能的返回值，包括：

- **0x0001.** Helper 标记用于打开上载作业的本地文件，创建或重命名下载作业的临时文件，或创建或重命名上传答复作业的答复文件。

- **0x0002.** Helper 标记用于打开服务器消息块（SMB）上传或下载作业的远程文件，或用于响应隐式 NTLM 或 Kerberos 凭据的 HTTP 服务器或代理质询。 必须调用/SetCredentialsJob TargetScheme NULL NULL，以允许通过 HTTP 发送凭据。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
