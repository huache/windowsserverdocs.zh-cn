---
title: Scwcmd 注册
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fe4d126a-9f27-4076-b7b1-fbefa45f378a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b7328a9db29f394bde089988ab0bdbcd84f54b30
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722144"
---
# <a name="scwcmd-register"></a>Scwcmd: register

> 适用于： Windows Server 2012 R2、Windows Server 2012

通过注册包含角色、任务、服务或端口定义的安全配置数据库文件来扩展或自定义安全配置向导（SCW）安全配置数据库。

## <a name="syntax"></a>语法

```
scwcmd register /kbname:<MyApp> [/kbfile:<kb.xml>] [/kb:<path>] [/d]
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|/kbname：\<MyApp>|指定将在其中注册安全配置数据库扩展的名称。 必须指定此参数。|
|/kbfile：\<Kb>|指定将用于扩展或自定义基本安全配置数据库的安全配置数据库文件的路径和文件名。 若要验证安全配置数据库文件与 SCW 架构是否兼容，请使用%windir%\security\KBRegistrationInfo.xsd 架构定义文件。 除非指定了 **/d**参数，否则必须提供此选项。|
|/kb：\<路径>|指定包含要更新的 SCW 安全配置数据库文件的目录的路径。 如果未指定此选项，则使用%windir%\security\msscw\kbs。|
|/d|从安全配置数据库中注销安全配置数据库扩展。 要取消注册的扩展是由/kbname 参数指定的。 （不应指定 **/kbfile**参数。）要从中注销扩展的安全配置数据库由 **/kb**参数指定。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

Scwcmd 仅适用于运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的计算机。

## <a name="examples"></a>示例

若要在 kbserver\kb 位置\\ \\的名称 MyApp 下注册名为 SCWKBForMyApp 的安全配置数据库文件，请键入：
```
scwcmd register /kbfile:d:\SCWKBForMyApp.xml /kbname:MyApp /kb:\\kbserver\kb
```
若要注销位于\\ \\kbserver\kb 的安全配置数据库 MyApp，请键入：
```
scwcmd register /d /kbname:MyApp /kb:\\kbserver\kb
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)