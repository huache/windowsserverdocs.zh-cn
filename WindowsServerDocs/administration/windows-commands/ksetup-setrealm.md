---
title: ksetup setrealm
description: Ksetup setrealm 命令的参考文章，用于设置 Kerberos 领域的名称。
ms.topic: reference
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 53de8c94e20f496a6f3078d3ad03a817f23e326a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025361"
---
# <a name="ksetup-setrealm"></a>ksetup setrealm

设置 Kerberos 领域的名称。

> [!IMPORTANT]
> 不支持在域控制器上设置 Kerberos 领域。 如果尝试这样做，将导致警告和命令失败。

## <a name="syntax"></a>语法

```
ksetup /setrealm <DNSdomainname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<DNSdomainname>` | 指定大写的 DNS 名称，例如 CORP。CONTOSO.COM。 您可以使用完全限定的域名或名称的简单形式。 如果不使用大写作为 DNS 名称，系统会要求进行验证以继续。 |

### <a name="examples"></a>示例

若要将此计算机的领域设置为特定域名，并将非域控制器的访问权限限制为 CONTOSO Kerberos 领域，请键入：

```
ksetup /setrealm CONTOSO
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup removerealm](ksetup-removerealm.md)
