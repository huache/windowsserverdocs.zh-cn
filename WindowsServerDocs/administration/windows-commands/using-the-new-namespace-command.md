---
title: 新命名空间
description: 用于创建和配置新命名空间的新命名空间的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6df60703-30bd-4d59-a8d9-9fe3efe96add
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3afbdd195f21450508bfa6992fc73c7d360092c6
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932410"
---
# <a name="new-namespace"></a>新命名空间

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建并配置新的命名空间。 当你只安装了传输服务器角色服务时，应使用此选项。 如果同时安装了 "部署服务器" 角色服务和 "传输服务器" 角色服务（这是默认设置），请使用[MulticastTransmission 命令](using-the-new-multicasttransmission-command.md)。 请注意，在使用此选项之前，必须注册该内容提供程序。
## <a name="syntax"></a>语法
```
wdsutil [Options] /New-Namespace [/Server:<Server name>]
     /FriendlyName:<Friendly name>
     [/Description:<Description>]
     /Namespace:<Namespace name>
     /ContentProvider:<Name>
     [/ConfigString:<Configuration string>]
     /Namespacetype: {AutoCast | ScheduledCast}
         [/time:<YYYY/MM/DD:hh:mm>]
         [/Clients:<Number of clients>]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|[/Server： <Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，则使用本地服务器。|
|友好<Friendly name>|指定命名空间的好记名称。|
|/Description<Description>]|设置命名空间的说明。|
|名称<Namespace name>|指定命名空间的名称。 请注意，这不是友好名称，并且必须是唯一的。<p>-   **部署服务器角色服务**：此选项的语法为/NAMESPACE： WDS： <Image group> / <Image name> / <Index> 。 例如： **WDS： ImageGroup1/install/1**<br />-   **传输服务器角色服务**：此值应与在服务器上创建命名空间时提供的名称匹配。|
|/ContentProvider： <Name> ]|指定将为命名空间提供内容的内容提供程序的名称。|
|[/ConfigString： <Configuration string> ]|指定内容提供商的配置字符串。|
|/Namespacetype： {自动广播 &#124; ScheduledCast}|指定传输的设置。 使用以下选项指定设置：<p>-[/time： <time> ]-使用以下格式设置传输应该开始的时间： YYYY/MM/DD： hh： MM。 此选项仅适用于计划强制转换传输。<br />-[/Clients： <Number of clients> ]-设置在传输开始之前要等待的最少客户端数。 此选项仅适用于计划强制转换传输。|
## <a name="examples"></a>示例
若要创建自动转换命名空间，请键入：
```
wdsutil /New-Namespace /FriendlyName:Custom AutoCast Namespace /Namespace:Custom Auto 1 /ContentProvider:MyContentProvider /Namespacetype:AutoCast
```
若要创建计划强制转换命名空间，请键入：
```
wdsutil /New-Namespace /Server:MyWDSServer /FriendlyName:Custom Scheduled Namespace /Namespace:Custom Auto 1 /ContentProvider:MyContentProvider
/Namespacetype:ScheduledCast /time:2006/11/20:17:00 /Clients:20
```
## <a name="additional-references"></a>其他参考
- [命令行语法关键字](command-line-syntax-key.md) 
[使用 AllNamespaces 命令](using-the-get-allnamespaces-command.md) 
[使用移除命名空间命令](using-the-remove-namespace-command.md) 
[子命令：起始-命名空间](subcommand-start-namespace.md)
