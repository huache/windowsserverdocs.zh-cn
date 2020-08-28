---
title: bitsadmin gethelpertokenflags
description: Bitsadmin gethelpertokenflags 命令的参考文章，它返回与 BITS 传输作业关联的帮助程序令牌的用法标志。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 59c6f2913c3c0f9bde3bbd591cf4a887e50af801
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033555"
---
# <a name="bitsadmin-gethelpertokenflags"></a>bitsadmin gethelpertokenflags

返回与 BITS 传输作业关联的帮助程序 [令牌](/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)的用法标志   。

> [!NOTE]
> BITS 3.0 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /gethelpertokenflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

### <a name="remarks"></a>注解

可能的返回值，包括：

- **0x0001.** Helper 标记用于打开上载作业的本地文件，创建或重命名下载作业的临时文件，或创建或重命名上传答复作业的答复文件。

- **0x0002.** Helper 标记用于打开服务器消息块 (SMB) 上传或下载作业的远程文件，或者用于响应针对隐式 NTLM 或 Kerberos 凭据的 HTTP 服务器或代理质询。 您必须调用  `/SetCredentialsJob TargetScheme NULL NULL`   以允许通过 HTTP 发送凭据。

## <a name="examples"></a>示例

若要检索与名为 *myDownloadJob*的 BITS 传输作业关联的帮助程序令牌的使用标志：

```
bitsadmin /gethelpertokenflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
