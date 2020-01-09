---
title: SMB 文件传输速度缓慢
description: 介绍如何排查 SMB 文件传输性能问题。
author: Deland-Han
manager: dcscontentpm
audience: ITPro
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 0e6c049404f464eba872075a8ef5060b303920c8
ms.sourcegitcommit: 8cf04db0bc44fd98f4321dca334e38c6573fae6c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75654558"
---
# <a name="slow-smb-files-transfer-speed"></a>SMB 文件传输速度缓慢

本文提供了通过 SMB 实现慢速文件传输速度的建议的故障排除过程。

## <a name="large-file-transfer-is-slow"></a>大型文件传输速度缓慢

如果观察到大文件传输缓慢，请考虑以下步骤：

- 对于未缓冲的 IO （**xcopy/j**或**robocopy/j**），请尝试文件复制命令。

- 测试存储速度。 这是因为文件复制速度受存储速度的限制。

- 文件副本有时会快速启动，然后速度会减慢。 按照以下准则验证此情况：
    
  - 这种情况通常发生在初始副本被缓存或缓冲的情况下（在内存中或在 RAID 控制器的内存缓存中），并且缓存会耗尽。这会强制将数据直接写入磁盘（写入）。 这是一个速度较慢的进程。
    
  - 使用存储性能监视器计数器来确定随着时间的推移，存储性能是否会下降。 有关详细信息，请参阅[SMB 文件服务器的性能优化](https://docs.microsoft.com/windows-server/administration/performance-tuning/role/file-server/smb-file-server)。

- 使用 RAMMap （SysInternals）可确定内存中 "映射的文件" 的使用是否因可用的内存消耗而停止增长。

- 查找跟踪中的数据包丢失情况。 这可能会导致 TCP 拥塞提供程序受到限制。

- 对于 SMBv3 和更高版本，请确保 SMB 多通道已启用且正常工作。

- 在 SMB 客户端上，在 SMB 中启用大型 MTU 并禁用带宽限制。 要执行此操作，请输入命令：  
  
  ```PowerShell
  Set-SmbClientConfiguration -EnableBandwidthThrottling 0 -EnableLargeMtu 1
  ```

## <a name="small-file-transfer-is-slow"></a>小文件传输速度缓慢

如果有多个文件，最常见的情况是通过 SMB 进行小文件的慢速传输。 这是预期的行为。

在文件传输过程中，创建文件会导致高协议开销和较高的文件系统开销。 对于大型文件传输，这些成本仅出现一次。 当传输大量小文件时，成本是重复的，导致传输速度缓慢。

下面是有关此问题的技术详细信息：

- SMB 调用 create 命令来请求创建文件。 某些代码将检查该文件是否存在，然后创建该文件。 或 create 命令的某些变体将创建实际文件。

- 每个 create 命令都会在文件系统上生成活动。

- 写入数据后，文件将关闭。

- 一段时间后，该过程将受到网络延迟和 SMB 服务器延迟的影响。 这是因为 SMB 请求首先转换为文件系统命令，然后转换为实际的文件系统延迟以完成操作。

- 如果任何防病毒程序正在运行，则传输的速度将更慢。 这是因为数据通常是通过数据包嗅探器一次扫描的，第二次将数据写入磁盘。 在某些情况下，这些操作是重复的。 你可能会发现小于 1 MB/秒的速度。

## <a name="opening-office-documents-is-slow"></a>打开 Office 文档速度缓慢

此问题通常发生在 WAN 连接上。 这种情况很常见，通常是由 Office 应用程序（特别是 Microsoft Excel）访问和读取数据的方式引起的。

建议确保办公室和 SMB 的二进制文件是最新的，然后通过在 SMB 服务器上禁用租约来进行测试。 要实现此目的，请执行下列步骤：
   
1. 在 Windows 8 和 Windows Server 2012 或更高版本的 Windows 中运行以下 PowerShell 命令：
      
   ```PowerShell
   Set-SmbServerConfiguration -EnableLeasing $false  
   ```
      
   或者，在提升的命令提示符窗口中运行以下命令：  

   ```cmd
   REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\lanmanserver\parameters /v DisableLeasing /t REG\_DWORD /d 1 /f  
   ```
      
   > [!NOTE]
   > 设置此注册表项后，不再授予 SMB2 租约，但 oplock 仍可用。 此设置主要用于故障排除。
    
2. 重新启动文件服务器或重新启动**服务器**服务。 若要重新启动该服务，请运行以下命令：

   ```cmd  
   NET STOP SERVER 
   NET START SERVER
   ```

若要避免此问题，还可以将文件复制到本地文件服务器。 有关详细信息，请参阅[使用 EFS 时 Aving Office 文档在网络服务器上的速度缓慢](https://docs.microsoft.com/office/troubleshoot/office/saving-file-to-network-server-slow)。
