---
title: ksetup delkpasswd
description: Ksetup delkpasswd 命令的参考主题，用于删除领域的 Kerberos 密码服务器（kpasswd）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2db0bfcd-bc08-48e3-9f30-65b6411839c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a84a70158ad707fb36d1ca8a4879a93fe0b7df06
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817837"
---
# <a name="ksetup-delkpasswd"></a>ksetup delkpasswd

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除领域的 Kerberos 密码服务器（kpasswd）。

## <a name="syntax"></a>语法

```
ksetup /delkpasswd <realmname> <kpasswdname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<realmname>` |  指定大写的 DNS 名称，例如 CORP。CONTOSO.COM，在**ksetup**运行时，将作为默认领域或**领域 =** 列出。 |
| `<kpasswdname>` | 指定 Kerberos 密码服务器。 它被表述为不区分大小写的完全限定的域名，例如 mitkdc.contoso.com。 如果省略了 KDC 名称，则可以使用 DNS 来查找 Kdc。 |

### <a name="examples"></a>示例

确保将领域公司CONTOSO.COM 使用非 Windows KDC 服务器 mitkdc.contoso.com 作为密码服务器，请键入：

```
ksetup /delkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```

确保将领域公司CONTOSO.COM 未映射到 Kerberos 密码服务器（KDC 名称），请 `ksetup` 在 Windows 计算机上键入，然后查看输出。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup delkpasswd 命令](ksetup-delkpasswd.md)
