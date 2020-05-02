---
title: bitsadmin gethelpertokenflags
description: Bitsadmin gethelpertokenflags 命令的参考主题，它返回与 BITS 传输作业关联的帮助程序令牌的用法标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 23e93ca71915fc369a940a21ce856b14deced004
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717909"
---
# <a name="bitsadmin-gethelpertokenflags"></a>bitsadmin gethelpertokenflags

返回与 BITS 传输作业关联的 [帮助程序令牌](https://docs.microsoft.com/windows/win32/bits/helper-tokens-for-bits-transfer-jobs) 的用法标志。

> [!NOTE]
> BITS 3.0 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /gethelpertokenflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

### <a name="remarks"></a>备注

可能的返回值，包括：

- **0x0001.** Helper 标记用于打开上载作业的本地文件，创建或重命名下载作业的临时文件，或创建或重命名上传答复作业的答复文件。

- **0x0002.** Helper 标记用于打开服务器消息块（SMB）上传或下载作业的远程文件，或用于响应隐式 NTLM 或 Kerberos 凭据的 HTTP 服务器或代理质询。 您必须调用 `/SetCredentialsJob TargetScheme NULL NULL` 以允许通过 HTTP 发送凭据。
  
## <a name="examples"></a>示例

若要检索与名为*myDownloadJob*的 BITS 传输作业关联的帮助程序令牌的使用标志：

```
bitsadmin /gethelpertokenflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
