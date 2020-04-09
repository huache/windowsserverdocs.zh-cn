---
title: ksetup： delkpasswd
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2db0bfcd-bc08-48e3-9f30-65b6411839c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b849265e6036f338413b75fe1da2067e4cdb4cd8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841650"
---
# <a name="ksetupdelkpasswd"></a>ksetup： delkpasswd

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

删除领域的 Kerberos 密码服务器（Kpasswd）。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。
## <a name="syntax"></a>语法
```
ksetup /delkpasswd <RealmName> <KpasswdName>
```
#### <a name="parameters"></a>参数

|   参数   |                                                                                                   说明                                                                                                   |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <RealmName>  |                                领域名称被声明为大写的 DNS 名称，例如 CORP。CONTOSO.COM，在**ksetup**运行时，将作为默认领域或领域 = 列出。                                |
| <KpasswdName> | 要用作 Kerberos 密码服务器的 KDC 名称被声明为不区分大小写的完全限定的域名，如 mitkdc.contoso.com。 如果省略了 KDC 名称，则可以使用 DNS 来查找 Kdc。 |

## <a name="remarks"></a>备注
运行命令**ksetup**来验证 KDC 名称。 如果**kpasswd =** 未出现在输出中，则表示尚未配置映射。 如果已设置，将列出多个映射。
## <a name="examples"></a><a name=BKMK_Examples></a>示例
验证领域 CORP。CONTOSO.COM 使用非 Windows KDC 服务器 mitkdc.contoso.com 作为密码服务器：
```
ksetup /delkpasswd CORP.CONTOSO.COM mitkdc.contoso.com
```
若要验证命令是否按预期运行，请在 Windows 计算机上运行**ksetup** ，以验证领域 CORP。CONTOSO.COM 未映射到 Kerberos 密码服务器（KDC 名称）。
## <a name="additional-references"></a>其他参考
-   [ksetup](ksetup.md)
-   [ksetup： delkpasswd](ksetup-delkpasswd.md)
-   - [命令行语法项](command-line-syntax-key.md)
