---
title: ksetup： delhosttorealmmap
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3faee482-a96c-4614-86fd-aaa446643ec4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2b6b14785f254a63f0e16fcd16f1cd464a2d69c8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724696"
---
# <a name="ksetupdelhosttorealmmap"></a>ksetup： delhosttorealmmap



删除所述主机和领域之间的服务主体名称（SPN）映射。

## <a name="syntax"></a>语法

```
ksetup /delhosttorealmmap <HostName> <RealmName>
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<主机名>|主机名是计算机的名称，可将其声明为计算机的完全限定的域名。|
|\<RealmName>|领域名称被声明为大写的 DNS 名称，例如 CORP。CONTOSO.COM。|

## <a name="remarks"></a>备注

当存在到领域（或多个主机到领域）映射的情况下，此命令将删除该映射。

该映射记录在注册表中**HKEY_LOCAL_MACHINE \system\currentcontolset\lsa\kerberos\hosttorealm**。 使用此命令后，应验证注册表中的映射。

## <a name="examples"></a>示例

更改领域 CONTOSO 的配置，删除主计算机 IPops897 到领域的映射：
```
ksetup /delhosttorealmmap IPops897 CONTOSO
```
运行此命令后，可以在注册表中验证映射是否按预期进行。

## <a name="additional-references"></a>其他参考

-   [Ksetup:addhosttorealmmap](ksetup-addhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)