---
title: Scwcmd 转换
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 640dd892-0bb9-416d-8318-60a26605bcf4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1fed9ff6369e6c966d9d1f5295db7db6648a1ab1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835120"
---
# <a name="scwcmd-transform"></a>Scwcmd: transform

> 适用于：Windows Server 2012 R2、Windows Server 2012

将使用安全配置向导（SCW）生成的安全策略文件转换为 Active Directory 域服务中的新组策略对象（GPO）。 转换操作不会更改执行它的服务器上的任何设置。 完成转换操作后，管理员必须将 GPO 链接到所需的 Ou，以将策略部署到服务器。

完成转换操作需要域管理员凭据。

> [!IMPORTANT]
> 无法使用组策略部署 Internet Information Services （IIS）安全策略设置。</br>除非在服务器上一次启动时 Windows 防火墙服务自动启动，否则不应将列出已批准的应用程序的 > 防火墙策略部署到服务器。

有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
scwcmd transform /p:<Policyfile.xml> /g:<GPODisplayName>
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/p：\<Policyfile >|指定应应用的 .xml 策略文件的路径和文件名。 必须指定此参数。|
|/g：\<GPODisplayName >|指定 GPO 的显示名称。 必须指定此参数。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

Scwcmd 仅适用于运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的计算机。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

若要从名为 FileServerPolicy 的文件中创建名为 FileServerSecurity 的 GPO，请键入：
```
scwcmd transform /p:FileServerPolicy.xml /g:FileServerSecurity
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)