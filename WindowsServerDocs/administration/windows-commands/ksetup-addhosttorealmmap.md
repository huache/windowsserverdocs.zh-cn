---
title: ksetup： addhosttorealmmap
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 237742d5-fa68-466c-b97e-636f489248ea
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1ee8f434482b0658194daed46b62f6f7f70abae1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841840"
---
# <a name="ksetupaddhosttorealmmap"></a>ksetup： addhosttorealmmap



在所述的主机和领域之间添加服务主体名称（SPN）映射。 有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
ksetup /addhosttorealmmap <HostName> <RealmName>
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<主机名 >|主机名是计算机的名称，可将其声明为计算机的完全限定的域名。|
|\<RealmName >|领域名称被声明为大写的 DNS 名称，例如 CORP。CONTOSO.COM。|

## <a name="remarks"></a>备注

此命令允许你将共享同一 DNS 后缀的一个或多个主机映射到领域。

该映射记录在注册表中**HKEY_LOCAL_MACHINE \system\currentcontolset\lsa\kerberos\hosttorealm**。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

在配置领域 CONTOSO 的过程中，将主机计算机 IPops897 映射到领域：
```
ksetup /addhosttorealmmap IPops897 CONTOSO
```
在注册表中验证映射是否按预期进行。

## <a name="additional-references"></a>其他参考

-   [Ksetup:delhosttorealmmap](ksetup-delhosttorealmmap.md)
-   [Ksetup](ksetup.md)
-   - [命令行语法项](command-line-syntax-key.md)