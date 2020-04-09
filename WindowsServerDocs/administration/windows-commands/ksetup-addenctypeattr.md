---
title: ksetup： addenctypeattr
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 32cc87d7-b9e1-4d14-9eb7-3b439c55aa3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 217e8a707c0af23901da3f433f630b253360f093
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841940"
---
# <a name="ksetupaddenctypeattr"></a>ksetup： addenctypeattr



将加密类型属性添加到域的可能类型列表中。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
ksetup /addenctypeattr <DomainName> {DES-CBC-CRC | DES-CBC-MD5 | RC4-HMAC-MD5 | AES128-CTS-HMAC-SHA1-96 | AES256-CTS-HMAC-SHA1-96}
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<DomainName >|要与之建立连接的域的名称。 使用完全限定的域名或名称的简单格式，如 corp.contoso.com 或 contoso。|
|加密类型|必须是以下受支持的加密类型之一：</br>-DES-CBC-CRC</br>-DES-CBC-MD5</br>-RC4-HMAC-MD5</br>-AES128--HMAC--SHA1-96</br>-AES256--HMAC--SHA1-96|

## <a name="remarks"></a>备注

若要查看 Kerberos 票证授予票证（TGT）的加密类型和会话密钥，请运行**klist**命令并查看输出。

可以通过使用空格将命令中的加密类型隔开，来设置或添加多个加密类型。 不过，每次只能对一个域执行此操作。

如果此命令成功或失败，将显示一条状态消息。

若要设置要连接到并使用的域，请运行**ksetup/domain \<DomainName >** 命令。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

确定在此计算机上设置的当前加密类型：
```
klist
```
将域设置为 corp.contoso.com：
```
ksetup /domain corp.contoso.com
```
将加密类型 AES-256-CTS-HMAC-SHA1-96 添加到域 corp.contoso.com 的可能类型列表中：
```
ksetup /addenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```
将域 corp.contoso.com 的 "加密类型" 属性设置为 "AES-256-CTS-HMAC-96-96"：
```
ksetup /setenctypeattr corp.contoso.com AES-256-CTS-HMAC-SHA1-96
```
验证已将 "加密类型" 属性设置为适用于域：
```
ksetup /getenctypeattr corp.contoso.com
```

## <a name="additional-references"></a>其他参考

-   [Klist](klist.md)
-   [Ksetup:domain](ksetup-domain.md)
-   [Ksetup:setenctypeattr](ksetup-setenctypeattr.md)
-   [Ksetup:getenctypeattr](ksetup-getenctypeattr.md)
-   [Ksetup:delenctypeattr](ksetup-delenctypeattr.md)
-   - [命令行语法项](command-line-syntax-key.md)