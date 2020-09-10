---
title: 使用 Windows Server Essentials 日志收集器
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: c6985518-b42d-4cfb-9761-eaa75306b6d7
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 07e849fa8db3cdc4204de402c6fc0cb823881480
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624995"
---
# <a name="use-the-windows-server-essentials-log-collector"></a>使用 Windows Server Essentials 日志收集器

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

当你解决计算机问题时，来自 Microsoft 客户服务和支持的代表可能会要求你使用 Windows Server Essentials 日志收集器从服务器、网络上的计算机或两者收集日志。

 日志收集器会将程序日志、事件查看器日志以及相关环境信息复制到位于指定位置的单个 zip 文件中。 你可以直接从服务器或网络上的任意计算机或者通过使用到计算机的远程连接运行日志收集器。

> [!NOTE]
>日志收集器不会分析网络问题或对任何服务器或网络上的计算机进行更改。 有关如何解决网络问题的信息，请参阅服务器产品的帮助文档。
>在本指南中，网络上的计算机（而不是服务器）称为 "网络计算机"。
>
>[下载 Windows Server Essentials 日志收集器安装包](https://www.microsoft.com/download/details.aspx?id=34821)。

 若要安装并运行日志收集器，请执行以下主题中的步骤：

1. [安装日志收集器](../support/Install-the-Windows-Server-Essentials-Log-Collector.md)

2. [运行日志收集器](../support/Run-the-Windows-Server-Essentials-Log-Collector.md)


## <a name="environment-information-collected"></a>已收集的环境信息
 对于你指定的每个网络计算机或服务器，日志收集器将收集以下环境信息并将其放置在日志集合文件中。

-   操作系统版本

-   CPU 制造商和说明

-   内存量和分配

-   绑定到 TCP/IP 的网络适配器

-   Locale

-   进程

-   存储配置

-   主机文件信息

-   包括应用程序、系统、Windows Server 和 Media Center 在内的事件日志

-   服务控制管理器消息

-   重新启动事件和 Windows Update 事件

-   系统错误和应用程序错误

## <a name="services-information-collected"></a>已收集的服务信息

### <a name="server-services"></a>服务器服务

-   Windows Server 客户端计算机备份服务

-   Windows Server 客户端计算机备份提供程序服务

-   Windows Server 设备提供程序

-   Windows Server 域名管理

-   Windows Server 服务提供程序注册表

-   Windows Server 设置提供程序

-   Windows Server UPnP 设备服务

-   Windows Server 远程 Web 访问管理提供程序

-   Windows Server 运行状况服务

-   Windows Server 存储服务

-   Windows Server SQM 服务

### <a name="network-computer-services"></a>网络计算机服务

-   Windows Server 客户端计算机备份提供程序服务

-   Windows Server 运行状况服务

-   Windows Server 服务提供程序注册表

-   Windows Server SQM 服务

## <a name="logs-and-registry-information-collected"></a>已收集的日志和注册表信息
 对于指定的每个网络计算机或服务器，日志收集器都将从服务器和网络计算机收集日志和注册表信息，如下所示。

### <a name="server-logs-and-registry-information"></a>服务器日志和注册表信息

-   服务器产品日志，来自 <ProgramData \> \Microsoft\Windows Server\Logs

-   计划任务

-   设置 API 日志

-   Windows Update 日志

-   运行状况警报文件

-   设备信息文件

-   服务器备份日志文件

-   Panther 日志文件

-   服务

-   注册表项，来自

    -   \\\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows 服务器 \

    -   \\\ HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\DevicesProviderSvc

    -   \\\ HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\DomainManagerProviderSvc

### <a name="network-computer-logs-and-registry-information"></a>网络计算机日志和注册表信息

-   <ProgramData \Microsoft\Windows Server\Logs 的网络计算机产品日志 \>

-   运行状况警报文件位于 <ProgramData \> \Microsoft\Windows Server\Data

-   Windows Update 日志

-   设置 API 日志

-   计划任务信息

-   \SOFTWARE\Microsoft\Windows 服务器 \ 中的注册表项 \ \\ HKEY_LOCAL_MACHINE \

## <a name="logs-for-computers-that-do-not-run-a-version-of-the-windows-operating-system"></a>未运行某个版本的 Windows 操作系统的计算机的日志
 日志收集器不会从未运行某个版本的 Windows 操作系统的计算机收集日志文件。 对于非 Windows 计算机，请将以下日志文件手动复制到要存储日志收集器文件的相同位置。

-   System.log

-   Library/Logs/Windows Server.log

-   Library/Logs/CrashReporter/快速启动板 <nnn \> (复制所有快速启动板 <nnn \> . 崩溃文件) 

-   Library/Logs/DiagnosticReports/快速启动板 <nnn \> (复制所有快速启动板 <nnn \> . 崩溃文件) 

## <a name="see-also"></a>请参阅

-   [日志收集器错误疑难解答](../support/Troubleshoot-Windows-Server-Essentials-Log-Collector-Errors.md)

