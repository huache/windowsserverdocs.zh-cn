---
title: Windows Server Essentials 的系统要求
description: 描述如何使用 Windows Server Essentials
ms.date: 10/31/2013
ms.topic: article
ms.assetid: 0951a67d-492f-41ad-9ae5-8e4cd25e3041
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: b82435dc9d0018d3ac3fa5c6855b18bcddbd2797
ms.sourcegitcommit: 04637054de2bfbac66b9c78bad7bf3e7bae5ffb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87838096"
---
# <a name="system-requirements-for-windows-server-essentials"></a>Windows Server Essentials 的系统要求

>适用于： Windows Server 2019 Essentials、Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

  Windows Server Essentials 服务器软件是仅限64位的操作系统。 表1定义了 Windows Server Essentials 的建议最低硬件要求。 表 2 规定了服务器的附加硬件和软件要求。


## <a name="table-1-system-requirements-for-windows-server-essentials"></a>表 1. Windows Server Essentials 的系统要求

|组件|最小值|建议配置*|最大值|
|---------------|-------------|-------------------|-------------|
|CPU 插座|1.4 GHz（64 位处理器）或更快（对于单核）<br /><br /> 1.3 GHz（64 位处理器）或更快（对于多核）|3.1 GHz（64 位处理器）或更快（对于多核）|2 个插座|
|内存 (RAM)|2 GB<br /><br /> 4 GB（如果要将 Windows Server Essentials 部署为虚拟机）|16 GB|64 GB|
|硬盘和可用存储空间|160 GB 硬盘，其中系统分区为 60 GB||无限制|

 *建议的硬件要求支持最大用户和设备限制。

## <a name="table-2-additional-hardware-and-software-requirements-for-windows-server-essentials"></a>表 2. Windows Server Essentials 的其他硬件和软件要求

|组件|说明|
|---------------|-----------------|
|网络适配器|千兆以太网适配器 (10/100/1000baseT PHY/MAC)|
|Internet|某些功能可能需要 Internet 访问（可能收费）或 Microsoft 帐户|
|支持的客户端操作系统|Windows 8.1、Windows 8、Windows 7、Macintosh OS X 版本 10.5 到 10.8。<br /><br /> **注意：** 某些功能需要专业版或更高版本。<br /><br /> 1 GB 的可用硬盘空间（安装后会释放此磁盘上的一个分区）|
|路由器|支持 IPv4 NAT 或 IPv6 的路由器或防火墙|
|其他需求|DVD-ROM 驱动器|

 实际要求将取决于系统配置以及选择安装的应用程序和功能。 处理器性能不仅取决于处理器的时钟频率，而且取决于内核数以及处理器缓存大小。 系统分区对存储空间只有大致的要求。 如果你正在通过网络进行安装，则可能需要其他可用存储空间。

 有关硬件要求的详细信息，请参阅 [Windows Server Catalog](https://www.windowsservercatalog.com/)。

 所有服务器硬件都应满足为系统的 Windows Server 2012 R2 徽标计划建立的要求。 有关详细信息，请参阅 [Windows 徽标计划](/previous-versions/windows/hardware/hck/dn641155(v=vs.85))。

> [!IMPORTANT]
> Windows Server Essentials 不支持动态磁盘。

## <a name="additional-references"></a>其他参考

-   [安装 Windows Server Essentials](../install/Install-Windows-Server-Essentials.md)

-   [Windows Server Essentials 的系统要求](system-requirements.md)