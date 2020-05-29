---
title: DHCP 客户端上的问题疑难解答
description: 此 artilce 介绍了如何排查 DHCP 客户端上的问题并收集数据。
ms.prod: windows-server
ms.service: na
manager: dcscontentpm
ms.technology: server-general
ms.date: 5/26/2020
ms.topic: article
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: a6064b9e497fcd54671292ade77a08c06ba42920
ms.sourcegitcommit: ef089864980a1d4793a35cbf4cbdd02ce1962054
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84150295"
---
# <a name="troubleshoot-problems-on-the-dhcp-client"></a>DHCP 客户端上的问题疑难解答

本文介绍如何解决 DHCP 客户端上出现的问题。

## <a name="troubleshooting-checklist"></a>故障排除清单

检查以下设备和设置：

  - 电缆已连接并且正常工作。

  - 已在客户端连接到的交换机上启用 MAC 筛选。

  - 网络适配器已启用。

  - 安装并更新了正确的网络适配器驱动程序。

  - DHCP 客户端服务已启动并正在运行。 若要进行检查，请运行**net start**命令，然后查找**DHCP 客户端**。

  - 客户端计算机上没有防火墙阻止端口67和 68 UDP。

## <a name="event-logs"></a>事件日志

检查 Microsoft Windows DHCP 客户端事件/操作和 Microsoft Windows DHCP 客户端事件/管理事件日志。 与 DHCP 客户端服务相关的所有事件都会发送到这些事件日志。  
Microsoft Windows DHCP 客户端事件位于 "**应用程序和服务日志**" 下的 "事件查看器中。

"Get-netadapter-IncludeHidden" PowerShell 命令提供了解释日志中列出的事件所需的信息。 例如，接口 ID、MAC 地址等。

## <a name="data-collection"></a>数据收集

建议在出现问题时同时在 DHCP 客户端和服务器端同时收集数据。 但是，根据实际问题，还可以通过在 DHCP 客户端或 DHCP 服务器上使用单个数据集来开始调查。

若要从服务器和受影响的客户端收集数据，请使用[Wireshark](https://www.wireshark.org/download.html)。 在 DHCP 客户端和 DHCP 服务器计算机上同时开始收集。

在出现问题的客户端上运行以下命令：

```console
ipconfig /release  
ipconfig /renew
```

然后，在客户端和服务器上停止 Wireshark。 检查生成的跟踪。 至少应告诉您通信停止的阶段。