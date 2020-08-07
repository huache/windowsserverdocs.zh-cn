---
title: ksetup delhosttorealmmap
description: Ksetup delhosttorealmmap 命令的参考文章，该命令删除所述主机和领域之间 (SPN) 映射的服务主体名称。
ms.topic: article
ms.assetid: 3faee482-a96c-4614-86fd-aaa446643ec4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 953a8d33a65bb9c5aafd4d549f762772bc059ba4
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87888003"
---
# <a name="ksetup-delhosttorealmmap"></a>ksetup delhosttorealmmap

删除所述主机和领域之间 (SPN) 映射的服务主体名称。 此命令还会删除主机到领域 (或多个主机到领域) 之间的任何映射。

该映射存储在下的注册表中 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentContolSet\Lsa\Kerberos\HostToRealm` 。 运行此命令后，建议确保映射显示在注册表中。

## <a name="syntax"></a>语法

```
ksetup /delhosttorealmmap <hostname> <realmname>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<hostname>` | 指定计算机的完全限定的域名。 |
| `<realmname>` | 指定大写的 DNS 名称，例如 CORP。CONTOSO.COM。 |

### <a name="examples"></a>示例

若要更改领域 CONTOSO 的配置，并删除主计算机 IPops897 到领域的映射，请键入：

```
ksetup /delhosttorealmmap IPops897 CONTOSO
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup addhosttorealmmap 命令](ksetup-addhosttorealmmap.md)
