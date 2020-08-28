---
title: Scwcmd 注册
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: fe4d126a-9f27-4076-b7b1-fbefa45f378a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fe54d69cde4607e2d99d4d1f0507fddd428bddd6
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037505"
---
# <a name="scwcmd-register"></a>Scwcmd: register

> 适用于： Windows Server 2012 R2、Windows Server 2012

通过注册包含角色、任务、服务或端口定义的安全配置数据库文件，扩展或自定义安全配置向导 (SCW) 安全配置数据库。

## <a name="syntax"></a>语法

```
scwcmd register /kbname:<MyApp> [/kbfile:<kb.xml>] [/kb:<path>] [/d]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/kbname\<MyApp>|指定将在其中注册安全配置数据库扩展的名称。 必须指定此参数。|
|/kbfile\<Kb.xml>|指定将用于扩展或自定义基本安全配置数据库的安全配置数据库文件的路径和文件名。 若要验证安全配置数据库文件与 SCW 架构是否兼容，请使用%windir%\security\KBRegistrationInfo.xsd 架构定义文件。 除非指定了 **/d** 参数，否则必须提供此选项。|
|/kb\<Path>|指定包含要更新的 SCW 安全配置数据库文件的目录的路径。 如果未指定此选项，则使用%windir%\security\msscw\kbs。|
|/d|从安全配置数据库中注销安全配置数据库扩展。 要取消注册的扩展是由/kbname 参数指定的。  (不应指定 **/kbfile** 参数。 ) 安全配置数据库从中注销扩展，由 **/kb** 参数指定。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>注解

Scwcmd.exe 仅适用于运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的计算机。

## <a name="examples"></a>示例

若要将名为 SCWKBForMyApp.xml 的安全配置数据库文件注册到 location kbserver\kb 中的名称 MyApp 下 \\ \\ ，请键入：
```
scwcmd register /kbfile:d:\SCWKBForMyApp.xml /kbname:MyApp /kb:\\kbserver\kb
```
若要注销位于 kbserver\kb 的安全配置数据库 MyApp \\ \\ ，请键入：
```
scwcmd register /d /kbname:MyApp /kb:\\kbserver\kb
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)