---
title: nlbmgr
description: Nlbmgr 命令的参考文章，可帮助你使用网络负载平衡管理器从一台计算机配置和管理网络负载平衡群集和所有群集主机。
ms.topic: reference
ms.assetid: 89cb8590-b7cf-4a27-89fa-0fa62ea1a1ca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5e9036a5fc4a0941445be4c9e9cf11c8064caa08
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023581"
---
# <a name="nlbmgr"></a>nlbmgr

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用网络负载平衡管理器，从一台计算机配置和管理网络负载平衡群集和所有群集主机。 你还可以使用此命令将群集配置复制到其他主机。

你可以从命令行使用**systemroot\System32**文件夹中安装的**nlbmgr.exe**命令行启动网络负载平衡管理器。

## <a name="syntax"></a>语法

```
nlbmgr [/noping][/hostlist <filename>][/autorefresh <interval>][/help | /?]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /noping | 阻止网络负载平衡管理器在尝试通过 (WMI) Windows Management Instrumentation 联系它们之前对这些主机进行 ping 操作。 如果已在所有可用的网络适配器上禁用了 Internet 控制消息协议 (ICMP) ，请使用此选项。 如果网络负载平衡管理器尝试与不可用的主机联系，则使用此选项将会出现延迟。 |
| /hostlist `<filename>` | 将 filename 中指定的主机加载到网络负载平衡管理器中。 |
| /autorefresh `<interval>` | 导致网络负载平衡管理器每隔一秒刷新其主机和群集信息 `<interval>` 。 如果未指定间隔，则信息每60秒刷新一次。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [NetworkLoadBalancingClusters cmdlet 参考](/powershell/module/networkloadbalancingclusters)
