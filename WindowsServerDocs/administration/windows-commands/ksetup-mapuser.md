---
title: ksetup： mapuser
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 84113e6e-89ff-488a-9cd0-f14bbf23b543
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: daa1b8d2c6d0ce2801191b953a533a63bcd8f4ab
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724618"
---
# <a name="ksetupmapuser"></a>ksetup： mapuser



将 Kerberos 主体的名称映射到帐户。

## <a name="syntax"></a>语法

```
ksetup /mapuser <Principal> <Account>
```

#### <a name="parameters"></a>参数

|  参数   |                                                   描述                                                   |
|--------------|-----------------------------------------------------------------------------------------------------------------|
| \<主体> |              任何主体的完全限定的域名;例如， mike@corp.CONTOSO.COM。              |
|  \<帐户>  | 此计算机上存在的任何帐户或安全组名称，如来宾、域用户或管理员。 |

## <a name="remarks"></a>备注

可以专门确定帐户，如域来宾。 您也可以使用通配符（*）包含所有帐户。

如果省略帐户名称，则会删除指定主体的映射。

如果用户提供有效的 Kerberos 票证，则计算机将仅对给定领域的主体进行身份验证。

使用不带任何参数或参数的**ksetup**查看当前映射的设置和默认领域。

每当对外部密钥发行中心（KDC）和领域配置进行更改时，都需要重新启动更改了设置的计算机。

## <a name="examples"></a>示例

将你的 Kerberos 领域中的 Mike Danseglio 的帐户映射到此计算机上的来宾帐户，向他授予内置来宾帐户成员的所有权限，而无需对此计算机进行身份验证：
```
ksetup /mapuser mike@corp.CONTOSO.COM guest
```
删除 Mike Danseglio 的帐户到此计算机上的来宾帐户的映射，以防止他通过 CONTOSO 提供的凭据对此计算机进行身份验证：
```
ksetup /mapuser mike@corp.CONTOSO.COM 
```
将 CONTOSO Kerberos 领域内的 Mike Danseglio 的帐户映射到此计算机上的任何现有帐户。 （如果此计算机上只有标准用户和来宾帐户处于活动状态，则 Mike 的权限将设置为这些帐户）：
```
ksetup /mapuser mike@corp.CONTOSO.COM *
```
将 CONTOSO Kerberos 领域内的所有帐户映射到此计算机上任何同名的现有帐户：
```
ksetup /mapuser * *
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Ksetup](ksetup.md)