---
title: ksetup delkpasswd
description: Ksetup delkpasswd 命令的参考文章，用于删除领域的 Kerberos 密码服务器 (kpasswd) 。
ms.topic: reference
ms.assetid: 2db0bfcd-bc08-48e3-9f30-65b6411839c6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 52624252953770ebe131a7c31618058232a21d05
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639675"
---
# <a name="ksetup-delkpasswd"></a>ksetup delkpasswd

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

为某个领域删除 Kerberos 密码服务器 (kpasswd) 。

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

确保将领域公司CONTOSO.COM 未映射到 Kerberos 密码服务器 (KDC 名称) ，请 `ksetup` 在 Windows 计算机上键入，然后查看输出。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup delkpasswd 命令](ksetup-delkpasswd.md)
