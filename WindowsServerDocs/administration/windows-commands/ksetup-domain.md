---
title: ksetup domain
description: 用于为所有 Kerberos 操作设置域名的 ksetup 域命令的参考文章。
ms.topic: reference
ms.assetid: 2ef766e3-6071-44f2-946b-22ea5b61a508
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: dcb7624f7b9fa81c66fed4533a0ba377095fa902
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640041"
---
# <a name="ksetup-domain"></a>ksetup domain

设置所有 Kerberos 操作的域名。

## <a name="syntax"></a>语法

```
ksetup /domain <domainname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<domainname>` | 要与之建立连接的域的名称。 使用完全限定的域名或名称的简单格式，如 contoso.com 或 contoso。|

### <a name="examples"></a>示例

若要使用子命令建立与有效域（如 Microsoft）的连接，请 `ksetup /mapuser` 键入：

```
ksetup /mapuser principal@realm domain-user /domain domain-name
```

成功连接后，会收到新的 TGT，否则将刷新现有的 TGT。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)

- [ksetup mapuser 命令](ksetup-mapuser.md)