---
title: ksetup： removerealm
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39f0c6f0-4c50-4781-941e-0893495405e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bb7bf4663594a6c164d6495a9ba4cd81942afb79
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724605"
---
# <a name="ksetupremoverealm"></a>ksetup： removerealm



从注册表中删除指定领域的所有信息。

## <a name="syntax"></a>语法

```
ksetup /removerealm <RealmName>
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<RealmName>|领域名称被声明为大写的 DNS 名称，例如 CORP。CONTOSO.COM，在**ksetup**运行时，它将作为默认领域列出。|

## <a name="remarks"></a>备注

领域名称存储在注册表中的两个位置： **HKEY_LOCAL_MACHINE \system\controlset001**和**\CurrentControlSet\Control\Lsa\Kerberos**。

你无法从域控制器中删除默认领域名称，因为这会重置其 DNS 信息，删除它可能会使域控制器不可用。

## <a name="examples"></a>示例

在本地计算机上错误地将领域名称设置为 "CORP"。CONTOSO.图标
```
ksetup /setrealm CORP.CONTOSO.CON
```
从本地计算机中删除该错误领域名：
```
ksetup /removerealm CORP.CONTOSO.CON
```
通过运行**ksetup**验证删除，并查看输出。

## <a name="additional-references"></a>其他参考

-   [Ksetup](ksetup.md)
-   [Ksetup:setrealm](ksetup-setrealm.md)
-   - [命令行语法项](command-line-syntax-key.md)