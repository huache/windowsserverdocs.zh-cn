---
title: ksetup： setrealm
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 453977ac39dd3a52b4f5a3104995f944e4a48392
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724549"
---
# <a name="ksetupsetrealm"></a>ksetup： setrealm



设置 Kerberos 领域的名称。

## <a name="syntax"></a>语法

```
ksetup /setrealm <DNSDomainName>
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<DNSDomainName>|DNS 域名的形式可以是完全限定的域名或简单的域名。|

## <a name="remarks"></a>备注

应以大写字母形式输入 DNS 域名参数。 否则， **ksetup**命令将要求确认才能继续。

不支持在域控制器上设置 Kerberos 领域。 尝试这样做将导致警告和命令失败。

## <a name="examples"></a>示例

将此计算机的 "领域" 设置为特定域名，以将非域控制器的访问权限限制为仅限 CONTOSO Kerberos 领域：
```
ksetup /setrealm CONTOSO
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Ksetup](ksetup.md)
-   [Ksetup:removerealm](ksetup-removerealm.md)