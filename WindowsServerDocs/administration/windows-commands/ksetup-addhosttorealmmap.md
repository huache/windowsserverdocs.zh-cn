---
title: ksetup addhosttorealmmap
description: Ksetup addhosttorealmmap 命令的参考文章，其中添加了一个服务主体名称 (SPN) 所述主机与领域之间的映射。
ms.topic: reference
ms.assetid: 237742d5-fa68-466c-b97e-636f489248ea
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 16ffe4431167ef63c73d4889febed49c40344e8b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639758"
---
# <a name="ksetup-addhosttorealmmap"></a>ksetup addhosttorealmmap

在所述的主机与领域之间 (SPN) 映射中添加服务主体名称。 此命令还允许你将共享同一 DNS 后缀的一个或多个主机映射到领域。

该映射存储在注册表中 **HKEY_LOCAL_MACHINE \system\currentcontolset\lsa\kerberos\hosttorealm**下。

## <a name="syntax"></a>语法

```
ksetup /addhosttorealmmap <hostname> <realmname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| `<hostname>` | 主机名是计算机的名称，可将其声明为计算机的完全限定的域名。 |
| `<realmname>` | 领域名称被声明为大写的 DNS 名称，例如 CORP。CONTOSO.COM。 |

### <a name="examples"></a>示例

若要将主计算机 *IPops897* 映射到 *CONTOSO* 领域，请键入：

```
ksetup /addhosttorealmmap IPops897 CONTOSO
```

检查注册表以确保按预期方式进行映射。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup delhosttorealmmap 命令](ksetup-delhosttorealmmap.md)
