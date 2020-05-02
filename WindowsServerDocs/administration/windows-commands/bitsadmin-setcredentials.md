---
title: bitsadmin setcredentials
description: Bitsadmin setcredentials 命令的参考主题，它将凭据添加到作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3cd099a4-9e85-46d8-8527-edb6dfab7f97
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4fbedcc65931e7d3cfb1719786f423b0d071b411
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719318"
---
# <a name="bitsadmin-setcredentials"></a>bitsadmin setcredentials

向作业添加凭据。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /setcredentials <job> <target> <scheme> <username> <password>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| 目标 | 使用**服务器**或**代理**。 |
| scheme | 使用下列其中一个：<ul><li>**BASIC.。** 身份验证方案，在此方案中，用户名和密码以明文形式发送到服务器或代理。</li><li>**摘要.** 质询-响应身份验证方案，该方案将服务器指定的数据字符串用于质询。</li><li>**NTLM.** 质询-响应身份验证方案，该方案使用用户的凭据在 Windows 网络环境中进行身份验证。</li><li>**协商（也称为简单和受保护的协商协议）。** 质询-响应身份验证方案，该方案与服务器或代理协商以确定要用于身份验证的方案。 例如，Kerberos 协议和 NTLM。</li><li>**通行证.** Microsoft 提供的一种集中式身份验证服务，可为成员站点提供单一登录。</li></ul> |
| user_name | 用户的名称。 |
| password | 与提供的*用户名*关联的密码。 |

## <a name="examples"></a>示例

若要将凭据添加到名为*myDownloadJob*的作业：

```
bitsadmin /setcredentials myDownloadJob SERVER BASIC Edward password20
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
