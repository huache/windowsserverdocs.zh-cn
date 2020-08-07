---
title: ksetup addenctypeattr
description: Ksetup addenctypeattr 命令的参考文章，可将加密类型属性添加到域的可能类型列表中。
ms.topic: article
ms.assetid: 32cc87d7-b9e1-4d14-9eb7-3b439c55aa3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d1520451b7802c5e7cdd308cf40e61de356d3fab
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87888152"
---
# <a name="ksetup-addenctypeattr"></a>ksetup addenctypeattr

将加密类型属性添加到域的可能类型列表中。 成功或失败完成时，将显示一条状态消息。

## <a name="syntax"></a>语法

```
ksetup /addenctypeattr <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<domainname>` | 要与之建立连接的域的名称。 使用完全限定的域名或名称的简单格式，如 corp.contoso.com 或 contoso。 |
| 加密类型 | 必须是以下受支持的加密类型之一：<ul><li>DES-CBC</li><li>DES-CBC-MD5</li><li>RC4-HMAC-MD5</li><li>AES128--HMAC--SHA1-96</li><li>AES256--HMAC--SHA1-96</li></ul> |

#### <a name="remarks"></a>备注

- 可以通过使用空格将命令中的加密类型隔开，来设置或添加多个加密类型。 不过，每次只能对一个域执行此操作。

### <a name="examples"></a>示例

若要查看 Kerberos 票证授予票证的加密类型 (TGT) 和会话密钥，请键入：

```
klist
```

若要将域设置为 corp.contoso.com，请键入：

```
ksetup /domain corp.contoso.com
```

若要将加密类型*AES-256-CTS-HMAC-SHA1-96*添加到域*corp.contoso.com*的可能类型的列表，请键入：

```
ksetup /addenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```

若要将域*corp.contoso.com*的 "加密类型" 属性设置为 " *AES-256-CTS-HMAC-96-96* "，请键入：

```
ksetup /setenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```

若要验证是否已将 "加密类型" 属性设置为适用于域的属性，请键入：

```
ksetup /getenctypeattr corp.contoso.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [klist 命令](klist.md)

- [ksetup 命令](ksetup.md)

- [ksetup 域命令](ksetup-domain.md)

- [ksetup setenctypeattr 命令](ksetup-setenctypeattr.md)

- [ksetup getenctypeattr 命令](ksetup-getenctypeattr.md)

- [ksetup delenctypeattr 命令](ksetup-delenctypeattr.md)
