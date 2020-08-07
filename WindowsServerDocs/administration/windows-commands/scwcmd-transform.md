---
title: Scwcmd 转换
description: '* * * * 的参考文章'
ms.topic: article
ms.assetid: 640dd892-0bb9-416d-8318-60a26605bcf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5af1f9d1f2ee5386da8b02f4142c156c3711852f
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87883098"
---
# <a name="scwcmd-transform"></a>Scwcmd: transform

> 适用于： Windows Server 2012 R2、Windows Server 2012

使用安全配置向导将生成的安全策略文件转换 (SCW) 到) 中 (GPO Active Directory 域服务的新组策略对象。 转换操作不会更改执行它的服务器上的任何设置。 完成转换操作后，管理员必须将 GPO 链接到所需的 Ou，以将策略部署到服务器。

完成转换操作需要域管理员凭据。

> [!IMPORTANT]
> 不能使用组策略部署 (IIS) 安全策略设置 Internet Information Services。</br>除非在服务器上一次启动时 Windows 防火墙服务自动启动，否则不应将列出已批准的应用程序的 > 防火墙策略部署到服务器。



## <a name="syntax"></a>语法

```
scwcmd transform /p:<Policyfile.xml> /g:<GPODisplayName>
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|/p\<Policyfile.xml>|指定应应用的 .xml 策略文件的路径和文件名。 必须指定此参数。|
|/g\<GPODisplayName>|指定 GPO 的显示名称。 必须指定此参数。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

Scwcmd.exe 仅适用于运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的计算机。

## <a name="examples"></a>示例

若要从名为 FileServerPolicy.xml 的文件中创建名为 FileServerSecurity 的 GPO，请键入：
```
scwcmd transform /p:FileServerPolicy.xml /g:FileServerSecurity
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)