---
title: ksetup removerealm
description: 用于从注册表中删除指定领域的所有信息的 ksetup removerealm 命令的参考文章。
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a755600bc0d1bdbc7a1b19bed041cb4a7c5dea90
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887821"
---
# <a name="ksetup-removerealm"></a>ksetup removerealm

从注册表中删除指定领域的所有信息。

领域名称存储在和下的注册表中 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001` `\CurrentControlSet\Control\Lsa\Kerberos` 。 默认情况下，注册表中不存在此项。 可以使用[ksetup addrealmflags](ksetup-addrealmflags.md)命令填充注册表。

> [!IMPORTANT]
> 无法从域控制器中删除默认的领域名称，因为这会重置其 DNS 信息，删除它可能会使域控制器不可用。

## <a name="syntax"></a>语法

```
ksetup /removerealm <realmname>
```
### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<realmname>` | 指定大写的 DNS 名称，例如 CORP。CONTOSO.COM，在**ksetup**运行时，将作为默认领域或**领域 =** 列出。 |

### <a name="examples"></a>示例

删除 ( 的错误领域名称。从本地计算机中，而不是 .COM) ，请键入：
```
ksetup /removerealm CORP.CONTOSO.CON
```

若要验证删除，你可以运行**ksetup**命令并查看输出。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup setrealm 命令](ksetup-setrealm.md)
