---
title: ipxroute
description: Ipxroute 命令的参考主题，该命令显示和修改有关 IPX 协议使用的路由表的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3a30304f-655e-43d2-a4ac-7568abf8975c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: afcb5064bc8d4eb4a3b4a8920fcfcf71591d7af5
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818317"
---
# <a name="ipxroute"></a>ipxroute

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示和修改有关 IPX 协议使用的路由表的信息。 使用不带参数的**ipxroute**显示发送到未知、广播和多播地址的数据包的默认设置。

## <a name="syntax"></a>语法

```
ipxroute servers [/type=x]
ipxroute ripout <network>
ipxroute resolve {guid | name} {GUID | <adaptername>}
ipxroute board= N [def] [gbr] [mbr] [remove=xxxxxxxxxxxx]
ipxroute config
```

### <a name="parameters"></a>参数
| 参数 | 说明 |
| ------- | -------- |
| 服务器`[/type=x]` | 显示指定服务器类型的服务访问点（SAP）表。 **x**必须是整数。 例如， `/type=4` 显示所有文件服务器。 如果未指定 **/type**，则 `ipxroute servers` 显示所有类型的服务器，并按服务器名称列出它们。 |
| 解决 `{GUID | name}``{GUID | adaptername}` | 将 GUID 的名称解析为其友好名称，或解析为其 GUID 的友好名称。 |
| 板 = *n* | 指定要为其查询或设置参数的网络适配器。 |
| def | 将数据包发送到所有路由广播。 如果数据包被传输到源路由表中没有的唯一媒体访问卡（MAC）地址，则默认情况下， **ipxroute**会将数据包发送到单路由广播。 |
| gbr | 将数据包发送到所有路由广播。 如果数据包传输到广播地址（FFFFFFFFFFFF），则默认情况下， **ipxroute**会将数据包发送到单路由广播。 |
| mbr | 将数据包发送到所有路由广播。 如果数据包传输到多播地址（C000xxxxxxxx），则默认情况下， **ipxroute**会将数据包发送到单路由广播。 |
| remove =*i* | 从源路由表中删除给定的节点地址。 |
| config | 显示有关配置了 IPX 的所有绑定的信息。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要显示工作站所连接到的网络段、工作站节点地址和所使用的帧类型，请键入：

```
ipxroute config
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
