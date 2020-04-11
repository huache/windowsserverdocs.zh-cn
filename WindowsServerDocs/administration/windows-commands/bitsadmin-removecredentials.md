---
title: bitsadmin removecredentials
description: 适用于 bitsadmin **removecredentials**的 Windows 命令主题，用于从作业中删除凭据。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4a78ce9a-1feb-4811-a000-cce81287b22b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1dbb25f0b0a19358b83a610c4684a3eb647c8232
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123099"
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

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |
| target | 使用**服务器**或**代理**。 |
| 方案 (scheme) | 使用以下项之一：<ul><li>**BASIC.。** 身份验证方案，在此方案中，用户名和密码以明文形式发送到服务器或代理。</li><li>**摘要.** 质询-响应身份验证方案，该方案将服务器指定的数据字符串用于质询。</li><li>**NTLM.** 质询-响应身份验证方案，该方案使用用户的凭据在 Windows 网络环境中进行身份验证。</li><li>**协商（也称为简单和受保护的协商协议）。** 质询-响应身份验证方案，该方案与服务器或代理协商以确定要用于身份验证的方案。 例如，Kerberos 协议和 NTLM。</li><li>**通行证.** Microsoft 提供的一种集中式身份验证服务，可为成员站点提供单一登录。</li></ul> |

## <a name="examples"></a>示例

下面的示例从名为*myDownloadJob*的作业中删除凭据。

```
C:\>bitsadmin /removecredentials myDownloadJob SERVER BASIC
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)