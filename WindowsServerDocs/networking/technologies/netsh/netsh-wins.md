---
title: Network Shell (Netsh) 示例批处理文件
description: 本主题介绍如何使用 Windows Server 2016 中的 Netsh 创建执行多个任务的批处理文件。
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: c94e37a4-3637-4613-9eb5-ed604e831eca
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 86fbe66978f7c09a332bba16a27a13fa029cb5a6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401920"
---
# <a name="network-shell-netsh-example-batch-file"></a>Network Shell \(Netsh\) 示例批处理文件

适用于：Windows Server 2016

本主题介绍如何使用 Windows Server 2016 中的 Netsh 创建执行多个任务的批处理文件。 在此示例批处理文件中，使用了 netsh wins 上下文  。

## <a name="example-batch-file-overview"></a>示例批处理文件概述

可以在批处理文件和其他脚本中将 Netsh 命令用于 Windows Internet 名称服务 \(WINS\)，以自动执行任务。 以下批处理文件示例演示如何将 Netsh 命令用于 WINS，以执行各种相关任务。

在此示例批处理文件中，WINS\-A 是 IP 地址为 192.168.125.30 的 WINS 服务器，而 WINS\-B 是 IP 地址为 192.168.0.189 的 WINS 服务器。

示例批处理文件会完成以下任务。

- 向 WINS\-A 添加 IP 地址为 192.168.0.205 的动态名称记录 (MY\_RECORD \[04h\])
- 将 WINS\-B 设置为 WINS\-A 的推送/请求复制伙伴
- 连接到 WINS\-B，然后将 WINS\-A 设置为 WINS\-B 的推送/请求复制伙伴
- 启动从 WINS\-A 到 WINS\-B 的推送复制
- 连接到 WINS\-B 以验证是否成功复制了新记录 MY\_RECORD

## <a name="netsh-example-batch-file"></a>Netsh 示例批处理文件

在下面的示例批处理文件中，包含注释的行加有“rem,”（表示注释）前缀。 Netsh 会忽略注释。

    rem: Begin example batch file.
    
    rem two WINS servers:
    
    rem (WINS-A) 192.168.125.30
    
    rem (WINS-B) 192.168.0.189
    
    rem 1. Connect to (WINS-A), and add the dynamic name MY\_RECORD \[04h\] to the (WINS-A) database.
    
    netsh wins server 192.168.125.30 add name Name=MY\_RECORD EndChar=04 IP={192.168.0.205}
    
    rem 2. Connect to (WINS-A), and set (WINS-B) as a push/pull replication partner of (WINS-A).
    
    netsh wins server 192.168.125.30 add partner Server=192.168.0.189 Type=2
    
    rem 3. Connect to (WINS-B), and set (WINS-A) as a push/pull replication partner of (WINS-B).
    
    netsh wins server 192.168.0.189 add partner Server=192.168.125.30 Type=2
    
    rem 4. Connect back to (WINS-A), and initiate a push replication to (WINS-B).
    
    netsh wins server 192.168.125.30 init push Server=192.168.0.189 PropReq=0
    
    rem 5. Connect to (WINS-B), and check that the record MY\_RECORD \[04h\] was replicated successfully.
    
    netsh wins server 192.168.0.189 show name Name=MY\_RECORD EndChar=04
    
    rem 6. End example batch file.

## <a name="netsh-wins-commands-used-in-the-example-batch-file"></a>示例批处理文件中使用的 Netsh WINS 命令

以下部分列出了此示例过程中使用的 netsh wins 命令  。

- server  . 将当前 WINS 命令行上下文转移到由其名称或 IP 地址指定的服务器。
- add name  . 在 WINS 服务器上注册名称。
- add partner  . 在 WINS 服务器上添加复制伙伴。
- init push  . 启动推送触发器并将其发送到 WINS 服务器。
- show name  . 显示 WINS 服务器数据库中特定记录的详细信息。  

有关详细信息，请参阅 [Network Shell (Netsh)](netsh.md)。
