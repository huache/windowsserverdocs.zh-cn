---
title: bitsadmin removecredentials
description: Bitsadmin removecredentials 命令的参考文章，用于从作业中删除凭据。
ms.topic: article
ms.assetid: 4a78ce9a-1feb-4811-a000-cce81287b22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2e2d9d045af51b273f7b64a8513daf3f8adb3895
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893353"
---
# <a name="bitsadmin-removecredentials"></a>bitsadmin removecredentials

从作业中删除凭据。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /removecredentials <job> <target> <scheme>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| 目标 | 使用**服务器**或**代理**。 |
| scheme | 使用下列其中一个：<ul><li>**BASIC.。** 身份验证方案，在此方案中，用户名和密码以明文形式发送到服务器或代理。</li><li>**摘要.** 质询-响应身份验证方案，该方案将服务器指定的数据字符串用于质询。</li><li>**NTLM.** 质询-响应身份验证方案，该方案使用用户的凭据在 Windows 网络环境中进行身份验证。</li><li>**协商 (也称为简单和受保护的协商协议) 。** 质询-响应身份验证方案，该方案与服务器或代理协商以确定要用于身份验证的方案。 例如，Kerberos 协议和 NTLM。</li><li>**通行证.** Microsoft 提供的一种集中式身份验证服务，可为成员站点提供单一登录。</li></ul> |

## <a name="examples"></a>示例

若要删除名为*myDownloadJob*的作业中的凭据：

```
bitsadmin /removecredentials myDownloadJob SERVER BASIC
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
