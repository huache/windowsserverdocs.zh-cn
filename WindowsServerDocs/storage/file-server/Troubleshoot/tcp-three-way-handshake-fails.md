---
title: SMB 连接期间的 TCP 三向握手失败
description: 介绍 SMB 连接期间的 TCP 三向握手失败。
author: Deland-Han
manager: dcscontentpm
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: cb88fa89344172cfc1ed036865a4496ed73e9a22
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80815320"
---
# <a name="tcp-three-way-handshake-failure-during-smb-connection"></a>SMB 连接期间的 TCP 三向握手失败

分析网络跟踪时，你会注意到存在一个传输控制协议（TCP）三向握手故障，导致 SMB 问题发生。 本文介绍如何解决此问题。

## <a name="troubleshooting"></a>故障排除

通常，原因是阻止流量的本地或基础结构防火墙。 在以下任一情况下都可能发生此问题。

## <a name="scenario-1"></a>方案 1

TCP SYN 数据包到达 SMB 服务器，但 SMB 服务器不返回 TCP SYN 确认数据包。

若要解决此问题，请执行以下步骤。

### <a name="step-1"></a>步骤 1

运行**netstat**或**NETTCPCONNECTION** ，确保 TCP 端口445上有一个应由系统进程拥有的侦听器。

```cmd
netstat -ano | findstr :445
```

```PowerShell
Get-NetTcpConnection -LocalPort 445
```

### <a name="step-2"></a>步骤 2

请确保服务器服务已启动且正在运行。

### <a name="step-3"></a>步骤 3

采用 Windows 筛选平台（WFP）捕获来确定哪个规则或程序正在删除流量。 为此，请在命令提示符窗口中运行以下命令：

```cmd
netsh wfp capture start
```

重现该问题，然后运行以下命令：

```cmd
netsh wfp capture stop
```

运行方案跟踪，并在 SMB 流量（TCP 端口445）上查找 WFP 丢弃。

或者，您可以删除防病毒程序，因为它们并非始终基于 WFP。

### <a name="step-4"></a>步骤 4

如果启用了 Windows 防火墙，请启用防火墙日志记录，以确定它是否记录了丢弃流量。

请确保在 "**高级安全 Windows 防火墙**" 中启用了相应的 "文件和打印机共享（SMB 内置）" 规则 \>**入站规则**"。

> [!NOTE]
> "Windows 防火墙" 可能称为 "Windows Defender 防火墙"，具体取决于计算机的设置方式。

## <a name="scenario-2"></a>方案2

TCP SYN 数据包永远不会到达 SMB 服务器。

在这种情况下，必须沿网络路径调查设备。 你可以分析在每个设备上捕获的网络跟踪，以确定哪个设备阻止了流量。
