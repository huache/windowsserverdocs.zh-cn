---
title: ksetup addkpasswd
description: Ksetup addkpasswd 命令的参考文章，用于为某个领域添加 Kerberos 密码（kpasswd）服务器地址。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d3196995-1b38-48ff-ba08-911cfab77317
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2db728684e713df35a39995c8ca95196f0b745ed
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925557"
---
# <a name="ksetup-addkpasswd"></a>ksetup addkpasswd

为某个领域添加 Kerberos 密码（kpasswd）服务器地址。

## <a name="syntax"></a>语法

```
ksetup /addkpasswd <realmname> [<kpasswdname>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<realmname>` | 指定大写的 DNS 名称，例如 CORP。CONTOSO.COM，在**ksetup**运行时，将作为默认领域或**领域 =** 列出。 |
| `<kpasswdname>` | 指定 Kerberos 密码服务器。 它被表述为不区分大小写的完全限定的域名，例如 mitkdc.contoso.com。 如果省略了 KDC 名称，则可以使用 DNS 来查找 Kdc。 |

#### <a name="remarks"></a>备注

- 如果工作站将对其进行身份验证的 Kerberos 领域支持 Kerberos 更改密码协议，则可以将运行 Windows 操作系统的客户端计算机配置为使用 Kerberos 密码服务器。

- 你可以一次添加一个其他 KDC 名称。

### <a name="examples"></a>示例

配置 CORP。CONTOSO.COM 领域若要使用非 Windows KDC 服务器 mitkdc.contoso.com 作为密码服务器，请键入：

```
ksetup /addkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```

若要验证是否已设置 KDC 名称，请键入， `ksetup` 然后查看输出，查找文本**kpasswd =**。 如果看不到文本，则表示尚未配置映射。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup delkpasswd 命令](ksetup-delkpasswd.md)
