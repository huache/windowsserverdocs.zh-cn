---
title: ksetup addhosttorealmmap
description: Ksetup addhosttorealmmap 命令的参考主题，它在规定的主机和领域之间添加服务主体名称（SPN）映射。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 237742d5-fa68-466c-b97e-636f489248ea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ee2639a5bb071bdd3d6ac3f6373e881c18f3bf9a
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818107"
---
# <a name="ksetup-addhosttorealmmap"></a>ksetup addhosttorealmmap

在所述的主机和领域之间添加服务主体名称（SPN）映射。 此命令还允许你将共享同一 DNS 后缀的一个或多个主机映射到领域。

该映射存储在注册表中**HKEY_LOCAL_MACHINE \system\currentcontolset\lsa\kerberos\hosttorealm**下。

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

若要将主计算机*IPops897*映射到*CONTOSO*领域，请键入：

```
ksetup /addhosttorealmmap IPops897 CONTOSO
```

检查注册表以确保按预期方式进行映射。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup delhosttorealmmap 命令](ksetup-delhosttorealmmap.md)
