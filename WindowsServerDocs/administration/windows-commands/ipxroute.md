---
title: ipxroute
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3a30304f-655e-43d2-a4ac-7568abf8975c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5a6d0cac3f835e86d40e03141c0da51d514ef0c6
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724799"
---
# <a name="ipxroute"></a>ipxroute

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示和修改有关 IPX 协议使用的路由表的信息。 使用不带参数的**ipxroute**显示发送到未知、广播和多播地址的数据包的默认设置。   
## <a name="syntax"></a>语法  
```  
ipxroute servers [/type=X]  
ipxroute ripout <Network>  
ipxroute resolve {guid | name} {GUID | <AdapterName>}  
ipxroute board= N [def] [gbr] [mbr] [remove=xxxxxxxxxxxx]  
ipxroute config  
```  
#### <a name="parameters"></a>参数  
|参数|描述|  
|-------|--------|  
|服务器 [/type = X]|显示指定服务器类型的服务访问点（SAP）表。  **X**必须是整数。 例如， **/type = 4**显示所有文件服务器。 如果未指定 **/type**， **ipxroute 服务器**会显示所有类型的服务器，并按服务器名称列出它们。|  
|ripout 网络|查看 IPX 堆栈的路由表并根据需要发出 rip 请求，以发现*网络*是否可访问。  *Network*是 IPX 网段号。|  
|解析 {GUID&#124; 名称} {GUID&#124; AdapterName}|将 GUID 的名称解析为其友好名称，或解析为其 GUID 的友好名称。|  
|板 = *N*|指定要为其查询或设置参数的网络适配器。|  
|def|将数据包发送到所有路由广播。 如果数据包被传输到源路由表中没有的唯一媒体访问卡（MAC）地址，则默认情况下， **ipxroute**会将数据包发送到单路由广播。|  
|gbr|将数据包发送到所有路由广播。 如果数据包传输到广播地址（FFFFFFFFFFFF），则默认情况下， **ipxroute**会将数据包发送到单路由广播。|  
|mbr|将数据包发送到所有路由广播。 如果数据包传输到多播地址（C000xxxxxxxx），则默认情况下， **ipxroute**会将数据包发送到单路由广播。|  
|remove = *i*|从源路由表中删除给定的节点地址。|  
|config|显示有关配置了 IPX 的所有绑定的信息。|  
|/?|在命令提示符下显示帮助。|  
## <a name="examples"></a>示例  
若要显示工作站所连接到的网络段、工作站节点地址和所使用的帧类型，请键入：  
```  
ipxroute config  
```  
## <a name="additional-references"></a>其他参考  
-   - [命令行语法项](command-line-syntax-key.md)  
