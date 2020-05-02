---
title: ksetup： addhosttorealmmap
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 237742d5-fa68-466c-b97e-636f489248ea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 732dccc868ca85b108ba443d912788a14dd0e107
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724771"
---
# <a name="ksetupaddhosttorealmmap"></a>ksetup： addhosttorealmmap



在所述的主机和领域之间添加服务主体名称（SPN）映射。

## <a name="syntax"></a>语法

```
ksetup /addhosttorealmmap <HostName> <RealmName>
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<主机名>|主机名是计算机的名称，可将其声明为计算机的完全限定的域名。|
|\<RealmName>|领域名称被声明为大写的 DNS 名称，例如 CORP。CONTOSO.COM。|

## <a name="remarks"></a>备注

此命令允许你将共享同一 DNS 后缀的一个或多个主机映射到领域。

该映射记录在注册表中**HKEY_LOCAL_MACHINE \system\currentcontolset\lsa\kerberos\hosttorealm**。

## <a name="examples"></a>示例

在配置领域 CONTOSO 的过程中，将主机计算机 IPops897 映射到领域：
```
ksetup /addhosttorealmmap IPops897 CONTOSO
```
在注册表中验证映射是否按预期进行。

## <a name="additional-references"></a>其他参考

-   [Ksetup:delhosttorealmmap](ksetup-delhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)