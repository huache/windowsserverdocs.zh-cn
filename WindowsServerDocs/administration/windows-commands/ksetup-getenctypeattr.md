---
title: ksetup getenctypeattr
description: Ksetup getenctypeattr 命令的参考主题，它检索域的 "加密类型" 属性。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6c7ec002-355e-474d-bc27-27215049f1a8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2acead4ff1179002303c18d4feff262080203a28
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817697"
---
# <a name="ksetup-getenctypeattr"></a>ksetup getenctypeattr

检索域的加密类型属性。 成功或失败完成时，将显示一条状态消息。

可以通过运行**klist**命令并查看输出来查看 Kerberos 票证授予票证（TGT）和会话密钥的加密类型。 可以通过运行命令来设置要连接和使用的域 `ksetup /domain <domainname>` 。

## <a name="syntax"></a>语法

```
ksetup /getenctypeattr <domainname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<domainname>` | 要与之建立连接的域的名称。 使用完全限定的域名或名称的简单格式，如 corp.contoso.com 或 contoso。 |

### <a name="examples"></a>示例

若要验证域的加密类型属性，请键入：

```
ksetup /getenctypeattr mit.contoso.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [klist 命令](klist.md)

- [ksetup 命令](ksetup.md)

- [ksetup 域命令](ksetup-domain.md)

- [ksetup addenctypeattr 命令](ksetup-addenctypeattr.md)

- [ksetup setenctypeattr 命令](ksetup-setenctypeattr.md)

- [ksetup delenctypeattr 命令](ksetup-delenctypeattr.md)
