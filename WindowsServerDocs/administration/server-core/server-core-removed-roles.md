---
title: 不在 Windows Server 中的角色、角色服务和功能-Server Core
description: 了解 Windows Server 服务器核心安装选项中未包含的角色和功能。
ms.mktglfcycl: manage
ms.sitesec: library
author: pronichkin
ms.author: artemp
ms.localizationpriority: medium
ms.date: 02/23/2018
ms.openlocfilehash: b810eb78055eeeeda62ef9e0f7d6fb82efa99d14
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90077764"
---
# <a name="roles-role-services-and-features-not-in-windows-server---server-core"></a>不在 Windows Server 中的角色、角色服务和功能-Server Core

> 适用于： Windows Server 2019、Windows Server 2016 和 Windows Server (半年通道) 

以下角色、角色服务和功能已从 Windows Server 的服务器核心安装选项中删除。 使用此信息来帮助确定服务器核心选项是否适用于您的环境。

> [!NOTE]
> 你还可以查看 [包含在服务器核心中](server-core-roles-and-services.md)的角色、角色服务和功能的列表。 这是一个非常大的列表，因此为了获得最佳结果，请在此列表中搜索你感兴趣的特定角色或功能。

## <a name="roles-not-in-server-core"></a>不在服务器核心中的角色

- 传真服务器 (**传真**) 
- MultiPoint Services (**MultiPointServerRole**) 
- 网络策略和访问服务 (**NPAS**) 
- *Windows Server 版本1803之前*Windows 部署服务 (**WDS**)  () 

## <a name="role-services-not-in-server-core"></a>不在服务器核心中的角色服务
请注意，某些远程桌面角色服务包含在 Server Core (连接代理、授权、虚拟化主机) ，但其他不 (网关、RD 会话主机、Web 访问) 。

- 打印和文件服务 \ 分布式扫描服务器 (**打印扫描-服务器**) 
- 打印和文件服务 \ Internet 打印 (**打印-internet**) 
- 远程桌面服务 \ 远程桌面网关 (**RDS-网关**) 
- 远程桌面服务 \ 远程桌面会话主机 (**RDS-Server**) 
- 远程桌面服务 \ 远程桌面 Web 访问 (**RDS-Web 访问**) 
- 角色服务 Web 服务器 (IIS) \ 管理工具 \ IIS 管理控制台 (**web** 管理控制台) 
- 角色服务 Web 服务器 (IIS) \ 管理工具 \ IIS 6 管理兼容性 \ IIS 6 管理控制台 (**Lgcy**) 
- **WDS**部署服务器 (Windows 部署服务 \ 部署) 
- *Windows Server 版本1803之前* (**WDS**传输)  (Windows 部署服务 \ 传输服务器) 

## <a name="features-not-in-server-core"></a>不在服务器核心中的功能
- 后台智能传输服务 (位) \ IIS 服务器扩展 (**位-iis-Ext**) 
- Bitlocker 网络解锁 (**bitlocker-NetworkUnlock**) 
- 直接播放 (**直销**) 
- Internet 打印客户端 (**internet-打印-客户端**) 
- Lpr 端口监视器 (**lpr-monitor**) 
- 消息队列 \ 消息队列服务 \ 多播支持 (**MSMQ-多播**) 
- RAS 连接管理器管理工具包 (**CMAK**) 
- 远程协助 (**远程协助**) 
- 远程服务器管理工具 \ 功能管理工具 \ SMTP 服务器工具 (**RSAT-smtp**) 
- 远程服务器管理工具 \ 功能管理工具 \ BitLocker 驱动器加密管理实用工具 \ BitLocker 驱动器加密工具 (**RSAT-功能工具-BitLocker-bitlocker-remoteadmintool**) 
- 远程服务器管理工具 \ 功能管理工具 \ BITS 服务器扩展工具 (**RSAT**) 
- 远程服务器管理工具 \ 功能管理工具 \ 网络负载平衡工具 (**RSAT-NLB**) 
- 远程服务器管理工具 \ 功能管理工具 \ SNMP 工具 (**RSAT-snmp**) 
- 远程服务器管理工具 \ 功能管理工具 \ WINS 服务器工具 (**RSAT-wins**) 
- 远程服务器管理工具 \ 角色管理工具 \ hyper-v 管理工具 \ hyper-v GUI 管理工具 (**hyper-v-工具**) 
- 远程服务器管理工具 \ 角色管理工具 \ 远程桌面服务工具 \ 远程桌面网关 Tools (**RSAT-tools**) 
- 远程服务器管理工具 \ 角色管理工具 \ 远程桌面服务工具 \ 远程桌面网关工具 (**RSAT-**) 
- 远程服务器管理工具 \ 角色管理工具 \ 远程桌面服务工具 \ 远程桌面许可诊断程序工具 (**RSAT-RDS-诊断-UI**) 
- 远程服务器管理工具 \ 角色管理工具 \ 远程桌面服务工具 \ 远程桌面授权工具 (**RDS-许可-UI**) 
- 远程服务器管理工具 \ 角色管理工具 \ Windows Server Update Services 工具 \ 用户界面管理控制台 (**updateservices-api**) 
- 远程服务器管理工具 \ 角色管理工具 \ Active Directory 证书服务工具 (**RSAT-ADCS**) 
- 远程服务器管理工具 \ 角色管理工具 \ Active Directory 证书服务工具 \ 证书颁发机构管理工具 (**RSAT-ADCS-管理**) 
- 远程服务器管理工具 \ 角色管理工具 \ Active Directory 证书服务工具 \ 联机响应程序工具 (**RSAT-联机响应程序**) 
- 远程服务器管理工具 \ 角色管理工具 \ Active Directory Rights Management Services 工具 (**RSAT-ADRMS**) 
- 远程服务器管理工具 \ 角色管理工具 \ 传真服务器工具 (**RSAT-传真**) 
- 远程服务器管理工具 \ 角色管理工具**\ 文件服务工具 () **
- 远程服务器管理工具 \ 角色管理工具 \ 文件服务工具 \ DFS 管理工具 (**RSAT-Dfs** 管理工具) 
- 远程服务器管理工具 \ 角色管理工具 \ 文件服务工具 \ 文件服务器资源管理器工具 (**RSAT-FSRM-管理**) 
- 远程服务器管理工具 \ 角色管理工具 \ 文件服务工具 \ 用于网络文件系统管理工具的服务 (**RSAT-NFS-管理员**) 
- 远程服务器管理工具 \ 角色管理工具 \ 网络策略和访问服务工具 (**RSAT-NPAS**) 
- 远程服务器管理工具 \ 角色管理工具 \ 打印和文件服务工具 (**RSAT-打印-服务**) 
- 远程服务器管理工具 \ 角色管理工具 \ 批量激活工具 (**RSAT-VA 工具**) 
- 远程服务器管理工具 \ 角色管理工具 \ Windows 部署服务 Tools (**WDS-AdminPack**) 
- 简单 TCP/IP 服务 (**简单的 TCPIP**) 
- SMTP 服务器 (**smtp-服务器**) 
- Tftp 客户端 (**tftp-客户端**) 
- Webdav 重定向 **程序 (webdav-重定向程序**) 
-  (**生物识别框架**) Windows Biometric Framework
- Windows defender 功能 \ 适用于 Windows Defender 的 GUI (**windows-Defender-GUI**) 
- Windows Identity Foundation 3.5 (**windows-Identity**) 
- Windows PowerShell \ Windows PowerShell ISE (**PowerShell-ISE**) 
- Windows 搜索服务 (**搜索-服务**) 
- Windows TIFF IFilter (**windows-TIFF-IFilter**) 
- 无线 LAN 服务 (**无线网络**) 
- Xps 查看器 (**xps-查看器**) 
