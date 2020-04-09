---
title: ksetup： addkpasswd
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d3196995-1b38-48ff-ba08-911cfab77317
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 73abfff54ecfcd31ebbd7469c12228fff850fbf1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841819"
---
# <a name="ksetupaddkpasswd"></a>ksetup： addkpasswd



为某个领域添加 Kerberos 密码（Kpasswd）服务器地址。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
ksetup /addkpasswd <RealmName> [<KpasswdName>]
```

#### <a name="parameters"></a>参数

如果工作站将对其进行身份验证的 Kerberos 领域支持 Kerberos 更改密码协议，则可以将运行 Windows 操作系统的客户端计算机配置为使用 Kerberos 密码服务器。 此设置是在领域端配置的。

|参数|说明|
|---------|-----------|
|\<RealmName >|领域名称被声明为大写的 DNS 名称，例如 CORP。CONTOSO.COM，在**ksetup**运行时，将作为默认领域或领域 = 列出。|
|\<KpasswdName >|要用作 Kerberos 密码服务器的 KDC 名称被声明为不区分大小写的完全限定的域名，例如 mitkdc.microsoft.com。 如果省略了 KDC 名称，则可以使用 DNS 来查找 Kdc。|

## <a name="remarks"></a>备注

如果工作站将对其进行身份验证的 Kerberos 领域支持 Kerberos 更改密码协议，则可以将运行 Windows 操作系统的客户端计算机配置为使用 Kerberos 密码服务器。

运行命令**ksetup**来验证 KDC 名称。 如果**kpasswd =** 未出现在输出中，则表示尚未配置映射。

你可以一次添加一个其他 KDC 名称。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

配置领域，公司。CONTOSO.COM，使其使用非 Windows KDC 服务器 mitkdc.contoso.com，作为密码服务器：
```
ksetup /addkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
这将生成一个非 Windows Kerberos 密码服务器，该服务器控制在其与领域之间进行身份验证的所有密码。

## <a name="additional-references"></a>其他参考

-   [Ksetup](ksetup.md)
-   [Ksetup:delkpasswd](ksetup-delkpasswd.md)
-   - [命令行语法项](command-line-syntax-key.md)