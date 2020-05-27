---
title: ksetup mapuser
description: Ksetup mapuser 命令的参考主题，它将 Kerberos 主体的名称映射到帐户。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 84113e6e-89ff-488a-9cd0-f14bbf23b543
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0ac2f3e30b3057ceea4376d7ffe8286875d5301d
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817667"
---
# <a name="ksetup-mapuser"></a>ksetup mapuser

将 Kerberos 主体的名称映射到帐户。

## <a name="syntax"></a>语法

```
ksetup /mapuser <principal> <account>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<principal>` | 指定任何主体用户的完全限定的域名。 例如，mike@corp.CONTOSO.COM。 如果未指定帐户参数，则将删除指定主体的映射。 |
| `<account>` | 指定此计算机上存在的任何帐户或安全组名称，如**来宾**、**域用户**或**管理员**。 如果省略此参数，则将删除指定主体的映射。 |

#### <a name="remarks"></a>备注

- 可以专门确定帐户（如**域来宾**），也可以使用通配符（*）包含所有帐户。

- 仅当给定领域的主体显示有效 Kerberos 票证时，计算机才会对其进行身份验证。

- 每当对外部密钥发行中心（KDC）和领域配置进行更改时，都需要重新启动更改了设置的计算机。

### <a name="examples"></a>示例

若要查看当前映射的设置和默认领域，请键入：

```
ksetup
```

若要将 Kerberos 领域 CONTOSO 中的 Mike Danseglio 帐户映射到此计算机上的来宾帐户，为他授予内置来宾帐户成员的所有权限，而无需对此计算机进行身份验证，请键入：

```
ksetup /mapuser mike@corp.CONTOSO.COM guest
```

若要删除此计算机上的 Danseglio 帐户与来宾帐户的映射，以防止他通过其来自 CONTOSO 的凭据对此计算机进行身份验证，请键入：

```
ksetup /mapuser mike@corp.CONTOSO.COM
```

若要将 CONTOSO Kerberos 领域中的 Mike Danseglio 帐户映射到此计算机上的任何现有帐户，请键入：

```
ksetup /mapuser mike@corp.CONTOSO.COM *
```

> [!NOTE]
> 如果此计算机上只有标准用户帐户和来宾帐户处于活动状态，则 Mike 的权限设置为这些帐户。

若要将 CONTOSO Kerberos 领域内的所有帐户映射到此计算机上任何同名的现有帐户，请键入：

```
ksetup /mapuser * *
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)
