---
title: ksetup： delkpasswd
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2db0bfcd-bc08-48e3-9f30-65b6411839c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2de1546b112041f7035a711852140e9bb34babe3
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724654"
---
# <a name="ksetupdelkpasswd"></a>ksetup： delkpasswd

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除领域的 Kerberos 密码服务器（Kpasswd）。
## <a name="syntax"></a>语法
```
ksetup /delkpasswd <RealmName> <KpasswdName>
```
#### <a name="parameters"></a>参数

|   参数   |                                                                                                   描述                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <RealmName>  |                                领域名称被声明为大写的 DNS 名称，例如 CORP。CONTOSO.COM，在**ksetup**运行时，将作为默认领域或领域 = 列出。                                |
| <KpasswdName> | 要用作 Kerberos 密码服务器的 KDC 名称被声明为不区分大小写的完全限定的域名，如 mitkdc.contoso.com。 如果省略了 KDC 名称，则可以使用 DNS 来查找 Kdc。 |

## <a name="remarks"></a>备注
运行命令**ksetup**来验证 KDC 名称。 如果**kpasswd =** 未出现在输出中，则表示尚未配置映射。 如果已设置，将列出多个映射。
## <a name="examples"></a>示例
验证领域 CORP。CONTOSO.COM 使用非 Windows KDC 服务器 mitkdc.contoso.com 作为密码服务器：
```
ksetup /delkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
若要验证命令是否按预期运行，请在 Windows 计算机上运行**ksetup** ，以验证领域 CORP。CONTOSO.COM 未映射到 Kerberos 密码服务器（KDC 名称）。
## <a name="additional-references"></a>其他参考
-   [ksetup](ksetup.md)
-   [ksetup： delkpasswd](ksetup-delkpasswd.md)
-   - [命令行语法项](command-line-syntax-key.md)
