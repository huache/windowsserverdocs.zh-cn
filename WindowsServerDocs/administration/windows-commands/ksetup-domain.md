---
title: ksetup 域
description: Ksetup 域命令的参考主题，用于为所有 Kerberos 操作设置域名。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ef766e3-6071-44f2-946b-22ea5b61a508
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1d497f2bc76bae8a95b077658c661e0fdc1e93f3
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817797"
---
# <a name="ksetup-domain"></a>ksetup 域

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