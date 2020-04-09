---
title: 删除-命名空间
description: 用于删除自定义命名空间的删除命名空间的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4eb758b6-8519-4e26-9fe0-2e19bb0e8702
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f8b830a5d99d13ed00a3a19f2cf246ad71d1c5f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80830230"
---
# <a name="using-the-remove-namespace-command"></a>使用移除命名空间命令

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

删除自定义命名空间。

## <a name="syntax"></a>语法
```
wdsutil /remove-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/force]
```
### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/Namespace：<Namespace name>|指定命名空间的名称。 这不是友好名称，并且必须是唯一的。<p>-   **部署服务器角色服务**：命名空间名称的语法为/NAMESPACE： WDS：<ImageGroup>/<ImageName>/<Index>。 例如： **WDS： ImageGroup1/install/1**<br />-   **传输服务器角色服务**：此值必须与在服务器上创建命名空间时为命名空间指定的名称相匹配。|
|[/Server：<Server name>]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，则使用本地服务器。|
|/force|立即删除命名空间并终止所有客户端。 请注意，除非指定 **/force**，否则现有的客户端可以完成传输，但无法加入新的客户端。|
## <a name="examples"></a><a name=BKMK_examples></a>示例
若要停止命名空间（当前客户端可以完成传输但新的客户端无法加入），请键入：
```
wdsutil /remove-Namespace /Namespace:Custom Auto 1
```
若要强制终止所有客户端，请键入：
```
wdsutil /remove-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /force
```
## <a name="additional-references"></a>其他参考
- [命令行语法键](command-line-syntax-key.md)
[使用 AllNamespaces 命令](using-the-get-allnamespaces-command.md)
[使用新的命名空间命令](using-the-new-namespace-command.md)
[子命令：起始-命名空间](subcommand-start-namespace.md)
