---
title: arp
description: Arp 命令的参考文章，其中显示和修改 address 解析协议中的条目 (arp) 缓存，用于存储 IP 地址及其已解决的物理地址。
ms.topic: reference
ms.assetid: 827e96eb-1945-483f-980f-714703456f7c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b97c285f36bac3fd8587abddaf0a70423eb26155
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029385"
---
# <a name="arp"></a>arp

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示和修改地址解析协议中的条目 (ARP) 缓存。 ARP 缓存包含一个或多个用于存储 IP 地址及其解析的以太网或令牌环物理地址的表。 计算机上安装的每个以太网或令牌环网络适配器都有一个单独的表。 在没有参数的情况下使用， **arp** 显示帮助信息。

## <a name="syntax"></a>语法

```
arp [/a [<inetaddr>] [/n <ifaceaddr>]] [/g [<inetaddr>] [-n <ifaceaddr>]] [/d <inetaddr> [<ifaceaddr>]] [/s <inetaddr> <etheraddr> [<ifaceaddr>]]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `[/a [<inetaddr>] [/n <ifaceaddr>]` | 显示所有接口的当前 arp 缓存表。 **/N**参数区分大小写。 若要显示特定 IP 地址的 arp 缓存条目，请将 **arp/a** 与 **inetaddr** 参数一起使用，其中 **inetaddr** 是一个 IP 地址。 如果未指定 **inetaddr** ，则使用第一个适用的接口。 若要显示特定接口的 arp 缓存表，请结合 **/a**参数使用 **/n ifaceaddr**参数，其中**inetaddr**是分配给接口的 IP 地址。 |
| `[/g [<inetaddr>] [/n <ifaceaddr>]` | 与 **/a**相同。 |
| `[/d <inetaddr> [<ifaceaddr>]` | 删除具有特定 IP 地址的条目，其中 **inetaddr** 是 ip 地址。 若要删除表中特定接口的条目，请使用 **ifaceaddr** 参数，其中 **ifaceaddr** 是分配给接口的 IP 地址。 若要删除所有条目，请使用星号 ( * ) 通配符替代 **inetaddr**。 |
| `[/s <inetaddr> <etheraddr> [<ifaceaddr>]` | 将一个静态条目添加到 arp 缓存，将 IP 地址 **inetaddr** 解析为物理地址 **etheraddr**。 若要为特定接口将静态 arp 缓存条目添加到表中，请使用 **ifaceaddr** 参数，其中 **ifaceaddr** 是分配给接口的 IP 地址。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="remarks"></a>注解

- **Inetaddr**和**ifaceaddr**的 IP 地址以点分隔的十进制表示法表示。

- **Etheraddr**的物理地址包含六个用十六进制表示法表示并由连字符分隔 (例如，00-AA-00-4F-9C) 。

- 用 **/s** 参数添加的条目是静态的，不会在 arp 缓存中超时。 如果已停止并启动 TCP/IP 协议，则会删除这些条目。 若要创建永久静态 arp 缓存条目，请将相应的 **arp** 命令放在批处理文件中，并使用计划任务在启动时运行批处理文件。

## <a name="examples"></a>示例

若要显示所有接口的 arp 缓存表，请键入：

```
arp /a
```

若要为分配了 IP 地址 *10.0.0.99*的接口显示 arp 缓存表，请键入：

```
arp /a /n 10.0.0.99
```

若要添加将 IP 地址 *10.0.0.80* 解析为物理地址 *00-AA-4F-9C*的静态 arp 缓存项，请键入：

```
arp /s 10.0.0.80 00-AA-00-4F-2A-9C
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
