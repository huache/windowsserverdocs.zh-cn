---
title: ksetup delkdc
description: Ksetup delkdc 命令的参考文章，用于删除 Kerberos 领域的密钥发行中心 (KDC) 名称的实例。
ms.topic: article
ms.assetid: 7d6ec389-094c-4a7b-a78b-605497ddc289
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f57e409afc62b831590f371befee2775f5c9cce9
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887972"
---
# <a name="ksetup-delkdc"></a>ksetup delkdc

删除 Kerberos 领域密钥发行中心 (KDC) 名称的实例。

该映射存储在下的注册表中 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\LSA\Kerberos\Domains` 。 运行此命令后，建议确保已删除 KDC，并不再显示在列表中。

> [!NOTE]
> 若要从多台计算机中删除领域配置数据，请将**安全配置模板**管理单元与策略分发一起使用，而不是在单独的计算机上显式使用**ksetup**命令。

## <a name="syntax"></a>语法

```
ksetup /delkdc <realmname> <KDCname>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<realmname>` | 指定大写的 DNS 名称，例如 CORP。CONTOSO.COM。 这是运行**ksetup**命令时显示的默认领域，它是要从中删除 KDC 的领域。 |
| `<KDCname>` | 指定区分大小写的完全限定的域名，例如 mitkdc.contoso.com。 |

### <a name="examples"></a>示例

若要查看 Windows 领域和非 Windows 领域之间的所有关联，并确定要删除的内容，请键入：

```
ksetup
```

若要删除关联，请键入：

```
ksetup /delkdc CORP.CONTOSO.COM mitkdc.contoso.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup addkdc 命令](ksetup-addkdc.md)