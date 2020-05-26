---
title: ksetup setenctypeattr
description: 用于设置域的加密类型属性的 ksetup setenctypeattr 命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 88fb913e-6b57-48d9-8c16-a035ab2977ac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e76ad3d08505208346ff2a3e100194239187953d
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817357"
---
# <a name="ksetup-setenctypeattr"></a>ksetup setenctypeattr

设置域的加密类型属性。 成功或失败完成时，将显示一条状态消息。

可以通过运行**klist**命令并查看输出来查看 Kerberos 票证授予票证（TGT）和会话密钥的加密类型。 可以通过运行命令来设置要连接和使用的域 `ksetup /domain <domainname>` 。

## <a name="syntax"></a>语法

```
ksetup /setenctypeattr <domainname> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<domainname>` | 要与之建立连接的域的名称。 使用完全限定的域名或名称的简单格式，如 corp.contoso.com 或 contoso。 |
| 加密类型 | 必须是以下受支持的加密类型之一：<ul><li>DES-CBC</li><li>DES-CBC-MD5</li><li>RC4-HMAC-MD5</li><li>AES128--HMAC--SHA1-96</li><li>AES256--HMAC--SHA1-96</li></ul> |

#### <a name="remarks"></a>备注

- 可以通过使用空格将命令中的加密类型隔开，来设置或添加多个加密类型。 不过，每次只能对一个域执行此操作。

### <a name="examples"></a>示例

若要查看 Kerberos 票证授予票证（TGT）的加密类型和会话密钥，请键入：

```
klist
```

若要将域设置为 corp.contoso.com，请键入：

```
ksetup /domain corp.contoso.com
```

若要将域 corp.contoso.com 的 "加密类型" 属性设置为 "AES-256-CTS-HMAC-96-96"，请键入：

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

- [ksetup addenctypeattr 命令](ksetup-addenctypeattr.md)

- [ksetup getenctypeattr 命令](ksetup-getenctypeattr.md)

- [ksetup delenctypeattr 命令](ksetup-delenctypeattr.md)
