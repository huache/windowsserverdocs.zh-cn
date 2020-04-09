---
title: Windows Server Essentials 日志收集器错误疑难解答
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: fa2e1685-31c0-4d4f-a10a-6c8885dfc493
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: e67071645e4ad00dc05c01836e25f223089d00c7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852220"
---
# <a name="troubleshoot-windows-server-essentials-log-collector-errors"></a>Windows Server Essentials 日志收集器错误疑难解答

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

运行日志收集器时，你可能会遇到以下错误之一。 若要解决某个问题，请按照针对相关联的错误提供的指南进行操作。  
  
> [!NOTE]
> 在本文档中，网络上的计算机（而不是服务器）称为 "网络计算机"。
  
###  <a name="the-destination-folder-is-not-valid"></a><a name="BKMK_TheDestinationFolderIsNotValid"></a>目标文件夹无效  
 **原因**：尝试复制日志文件的文件夹可能不存在，或者可能没有足够的空间来保存这些文件。  
  
 **解决方案** ：检查所选的文件夹是否存在以及驱动器上是否有足够的可用空间用于保存这些文件。 你还应该确保驱动器上的临时文件夹中剩余了足够的可用空间。  
  
###  <a name="a-network-error-has-occurred"></a><a name="BKMK_ANetworkErrorHasOccurred"></a>出现网络错误  
 **原因**：网络计算机或服务器上可能存在与网络相关的问题。  
  
 **解决方案**：确保所有计算机和网络设备的电源都已打开，并且它们已连接到网络。 如果你无法解决此问题，请联系你的网络维护人员以获取帮助。  
  
###  <a name="cannot-collect-log-files-for-the-computer"></a><a name="BKMK_CannotCollectLogFiles"></a>无法收集计算机的日志文件  
 **原因** ：由于计算机未使用“将计算机连接到服务器”向导成功连接到服务器，日志收集器可能未安装在该计算机上。  
  
 **解决方案：** 有关如何解决与服务器连接相关的问题的信息，请参阅将[计算机连接到服务器疑难解答](https://go.microsoft.com/fwlink/p/?LinkID=241492)。  
  
 如果你仍然无法将计算机连接到服务器，那么你可以将日志文件手动复制到 U 盘，如下所示：  
  
-   对于运行 Windows 7、Windows 8 或 Windows Multipoint Server 的客户端计算机，你可以复制位于 **%sysdir%\programdata\Microsoft\Windows Server** 的“日志”文件夹。  
  
###  <a name="you-do-not-have-permission-to-save-the-log-files-to-the-selected-folder"></a><a name="BKMK_YouDoNotHavePermission"></a>你没有将日志文件保存到所选文件夹的权限  
 **原因**：你可能不具有对用于保存日志文件的所选文件夹的写入权限。  
  
 **解决方案：** 如果使用默认路径保存日志文件，请确保对共享文件夹具有写入权限， **\\\\< ServerName\>\Logs**。 如果你要在网络计算机上存储日志，请确保你拥有对用于保存日志文件的所选文件夹的写入权限。  
  
###  <a name="the-computer-is-not-configured-properly-to-collect-the-log-files"></a><a name="BKMK_TheComputerIsNotConfiguredProperly"></a>计算机未正确配置，无法收集日志文件  
 **原因** ：计算机未针对日志收集器进行正确配置。  
  
 **解决方案**：重新安装日志收集器。 请参阅[重新安装日志收集器](Install-the-Windows-Server-Essentials-Log-Collector.md#BKMK_Reinstall)。  
  
###  <a name="an-unknown-error-occurred"></a><a name="BKMK_AnUnknownErrorOccurred"></a>出现未知错误  
 **原因**：未知。  
  
 **解决方案 1**：重新运行日志收集器。 如果再次发生错误，请确保不存在连接性问题。 你还可以尝试重新安装日志收集器。 请参阅[重新安装日志收集器](Install-the-Windows-Server-Essentials-Log-Collector.md#BKMK_Reinstall)。 如果你无法解决此问题，请联系你的网络维护人员以获取帮助。  
  
 **解决方案 2**：首先，尝试打开保存日志文件的文件夹。 如果已生成带有计算机名称的 zip 文件，则忽略此错误并改用日志文件。 如果未生成日志文件，则重新运行日志收集器。 如果再次发生错误，请确保不存在连接性问题。 你还可以尝试重新安装日志收集器。 请参阅[重新安装日志收集器](Install-the-Windows-Server-Essentials-Log-Collector.md#BKMK_Reinstall)。 如果你无法解决此问题，请联系你的网络维护人员以获取帮助。