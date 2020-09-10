---
title: Windows Server Essentials 最佳做法分析器 (BPA) 工具所使用的规则
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 37e1dae7-586c-4dd7-bf83-7e14a9567c8f
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 231fad84ecb5ac5831d4d638af7bd8fbe0281b04
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625540"
---
# <a name="rules-used-by-the-windows-server-essentials-best-practices-analyzer-bpa-tool"></a>Windows Server Essentials 最佳做法分析器 (BPA) 工具所使用的规则

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本文介绍 Windows Server Essentials 最佳做法分析器 (BPA) 所使用的规则。 BPA 检查正在运行 Windows Server Essentials 的服务器，并提供一份描述问题的报告，并提供解决这些问题的建议。 建议由适用于 Windows Server Essentials 的产品支持组织开发。

## <a name="using-the-tool"></a>使用工具
 这是一种标准做法，当你从 Windows Server 2011 Essentials、Windows Small Business Server 2011 Essentials 或 Windows Home Server 2011 迁移到 Windows Server Essentials 时，将在你完成设置和数据的迁移后在目标服务器上运行 BPA。 你可以随时从仪表板运行该工具。

#### <a name="to-run-the--windows-server-essentials-bpa-on-the-server"></a>在服务器上运行 Windows Server Essentials BPA

1.  以管理员身份登录到服务器，然后打开仪表板。

2.  在仪表板上单击“设备”**** 选项卡。

3.  在“服务器任务”**** 窗格中，单击“最佳做法分析器”****。

4.  查看每个 BPA 消息，并按照说明来解决问题（如有必要）。

## <a name="rules-used-by-the-best-practices-analyzer"></a>最佳做法分析器所使用的规则

### <a name="disable-ip-filtering"></a>禁用 IP 筛选
 **问题：** IP 筛选当前已在服务器上启用。 必须禁用 IP 筛选。

 **影响：** 如果启用 IP 筛选，则可能会阻止网络流量。

 **解决方法：**

##### <a name="to-disable-ip-filtering"></a>禁用 IP 筛选

1.  在服务器上打开 regedit.exe。

2.  导航到 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters。

3.  右键单击“启用安全筛选器”****，然后单击“修改”****。

4.  在“编辑 DWORD (32 位)值”**** 窗口中，将“值数据”**** 字段更改为零，然后单击“确定”****。

5.  若要应用更改，请重新启动服务器。

### <a name="the-distributed-transaction-coordinator-msdtc-service-should-be-set-to-start-automatically-by-default"></a>Distributed Transaction Coordinator (MSDTC) 服务应设置为默认情况下自动启动
 **问题：** MSDTC 服务未配置为自动启动

 **影响：** MSDTC 服务在服务器启动时可能无法自动启动。 如果该服务停止，某些 SQL Server 或 COM 功能可能会失败。 因此，使用 Microsoft SQL Server 或 COM 功能的应用程序可能无法正常工作。

 **解决方法：**

##### <a name="to-configure-the-msdtc-service-to-start-automatically"></a>将 MSDTC 服务配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击 **Distributed Transaction Coordinator** 服务，然后单击“属性”****。

3.  在“常规”**** 选项卡上，将“启动类型”**** 更改为“自动(延迟启动)”****，然后单击“确定”****。

### <a name="the-netlogon-service-should-be-configured-to-start-automatically-by-default"></a>Netlogon 服务应配置为默认情况下自动启动
 **问题：** Netlogon 服务未配置为自动启动。

 **影响：**  服务器启动时，Netlogon 服务可能无法自动启动。 如果该服务停止，则服务器可能不会对用户和服务进行身份验证。

 **解决方法：**

##### <a name="to-configure-the-netlogon-service-to-start-automatically"></a>将 Netlogon 服务配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“Netlogon”**** 服务，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="the-dns-client-service-should-be-configured-to-start-automatically-by-default"></a>DNS Client 服务应配置为默认情况下自动启动
 **问题：**  DNS 客户端服务未配置为自动启动。

 **影响：**  DNS 客户端服务可能不会在服务器启动时自动启动。 如果此服务停止，则服务器可能无法解析 DNS 名称。

 **解决方法：**

##### <a name="to-configure-the-dns-client-service-to-start-automatically"></a>将 DNS Client 服务配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“DNS Client”**** 服务，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="the-dns-server-service-should-be-configured-to-start-automatically-by-default"></a>DNS Server 服务应配置为默认情况下自动启动
 **问题：**  DNS 服务器服务未配置为自动启动。

 **影响：**  服务器启动时，DNS 服务器服务可能无法自动启动。 如果此服务停止，将不会进行 DNS 更新。

 **解决方法：**

##### <a name="to-configure-the-dns-server-service-to-start-automatically"></a>将 DNS Server 服务配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“DNS Server”**** 服务，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="active-directory-web-services-is-not-set-to-the-default-start-mode"></a>Active Directory Web Services 未设置为默认启动模式
 **问题：**  Active Directory Web 服务未设置为自动的默认启动模式。

 **影响：**  Active Directory Web Services (ADWS) 未设置为 "自动" 的默认启动模式。 如果服务器上的 ADWS 已停止或禁用，客户端应用程序（例如 Windows PowerShell 的 Active Directory 模块或 Active Directory 管理中心）则无法访问或管理在此服务器上运行的目录服务实例。 有关详细信息，请参阅 Windows Server 技术库中 [AD DS： Active Directory Web 服务 (中的新增功能](https://technet.microsoft.com/library/dd391908\(WS.10\).aspx) https://technet.microsoft.com/library/dd391908(WS.10).aspx) 。

 **解决方法：**

##### <a name="to-configure-the-active-directory-web-services-service-to-start-automatically"></a>将 Active Directory Web Services 服务配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“Active Directory Web Services”**** 服务，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="the-dhcp-client-service-should-be-configured-to-start-automatically-by-default"></a>DHCP Client 服务应配置为默认情况下自动启动
 **问题：**  DHCP 客户端服务未配置为自动启动。

 **影响：**  服务器启动时，DHCP 客户端服务不会自动启动。 如果此服务停止，客户端计算机则无法从服务器接收 IP 地址。

 **解决方法：**

##### <a name="to-configure-the-dhcp-client-service-to-start-automatically"></a>将 DHCP Client 服务配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“DHCP Client”**** 服务，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="the-iis-admin-service-should-be-configured-to-start-automatically-by-default"></a>IIS Admin Service 应配置为默认情况下自动启动
 **问题：** IIS 管理服务未配置为自动启动。

 **影响：** 服务器启动时，IIS 管理服务不会自动启动。 如果此服务停止，你可能无法访问在服务器上运行的网站，例如“远程 Web 访问”。

 **解决方法：**

##### <a name="to-configure-the-iis-admin-service-to-start-automatically"></a>将 IIS Admin Service 配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“IIS Admin Service”****，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="the-world-wide-web-publishing-service-should-be-configured-to-start-automatically-by-default"></a>World Wide Web Publishing Service 应配置为默认情况下自动启动
 **问题：**  World Wide Web 发布服务未配置为自动启动。

 **影响：**  World Wide Web 发布服务可能无法在服务器启动时自动启动。 如果此服务停止，你可能无法访问在服务器上运行的网站，例如“远程 Web 访问”。

 **解决方法：**

##### <a name="to-configure-the-world-wide-web-publishing-service-to-start-automatically"></a>将 World Wide Web Publishing Service 配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“World Wide Web Publishing Service”****，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="the-remote-registry-service-should-be-configured-to-start-automatically-by-default"></a>Remote Registry 服务应配置为默认情况下自动启动
 **问题：**  远程注册表服务未配置为自动启动。

 **影响：**

 Remote Registry 服务在服务器启动时可能无法自动启动。 如果此服务停止，你可能无法远程执行某些网络操作。

 **解决方法：**

##### <a name="to-configure-the-remote-registry-service-to-start-automatically"></a>将 Remote Registry 配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“Remote Registry”**** 服务，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="the-remote-desktop-gateway-service-should-be-configured-to-start-automatically-by-default"></a>Remote Desktop Gateway 服务应配置为默认情况下自动启动
 **问题：**  远程桌面网关服务未配置为自动启动。

 **影响：**  如果此服务已停止，则用户可能无法使用远程 Web 访问访问计算机。

 **解决方法：**

##### <a name="to-configure-the-remote-desktop-gateway-service-to-start-automatically"></a>将 Remote Desktop Gateway 服务配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“Remote Desktop Gateway”**** 服务，然后单击“属性”****。

3.  在“常规”**** 选项卡上，将“启动类型”**** 更改为“自动(延迟启动)”****，然后单击“确定”****。

### <a name="the-windows-time-service-should-be-configured-to-start-automatically-by-default"></a>Windows Time 服务应配置为默认情况下自动启动
 **问题：**  Windows 时间服务未配置为自动启动。

 **影响：**  如果此服务已停止，则数据和时间同步将不可用。

 **解决方法：**

##### <a name="to-configure-the-windows-time-service-to-start-automatically"></a>将 Windows Time 服务配置为自动启动

1.  在服务器上打开 services.msc。

2.  右键单击“Windows Time”**** 服务，然后单击“属性”****。

3.  在 **“常规”** 选项卡中，将 **“启动类型”** 更改为 **“自动”**，然后单击 **“确定”**。

### <a name="the-distributed-transaction-coordinator-msdtc-service-should-be-started"></a>应启动 Distributed Transaction Coordinator (MSDTC) 服务
 **问题：**  MSDTC 服务未在服务器上运行。

 **影响：**  如果此服务停止，某些 SQL Server 或 COM 功能可能会失败。 因此，使用 Microsoft SQL Server 或 COM 功能的应用程序可能无法正常工作。

 **解决方法：**

##### <a name="to-start-the-distributed-transaction-coordinator-service"></a>启动分布式事务处理协调器服务

1.  在服务器上打开 services.msc。

2.  右键单击“Distributed Transaction Coordinator”**** 服务，然后单击“启动”****。

### <a name="the-netlogon-service-should-be-started"></a>应启动 Netlogon 服务
 **问题：**  Netlogon 服务未在服务器上运行。

 **影响：**  如果该服务未启动，则服务器可能不会对用户和服务进行身份验证。

 **解决方法：**

##### <a name="to-start-the-netlogon-service"></a>启动 Netlogon 服务

1.  在服务器上打开 services.msc。

2.  右键单击“Netlogon”**** 服务，然后单击“启动”****。

### <a name="the-dns-client-service-should-be-started"></a>应启动 DNS Client 服务
 **问题：**  DNS 客户端服务未在服务器上运行。

 **影响：**  如果该服务未启动，则服务器可能无法解析 DNS 名称。

 **解决方法：**

##### <a name="to-start-the-dns-client-service"></a>启动 DNS Client 服务

1.  在服务器上打开 services.msc。

2.  右键单击“DNS Client”**** 服务，然后单击“启动”****。

### <a name="the-dns-server-service-should-be-started"></a>应启动 DNS Server 服务
 **问题：**  DNS 服务器服务未在服务器上运行。

 **影响：**  如果 DNS 服务器服务未启动，则可能无法进行 DNS 更新。

 **解决方法：**

##### <a name="to-start-the-dns-server-service"></a>启动 DNS Server 服务

1.  在服务器上打开 services.msc。

2.  右键单击“DNS Server”**** 服务，然后单击“启动”****。

### <a name="active-directory-web-services-is-not-started"></a>Active Directory Web Services 未启动
 **问题：**  未启动 Active Directory Web 服务。

 **影响：**  未启动 Active Directory Web 服务 (ADWS) 。 如果服务器上的 ADWS 已停止或禁用，客户端应用程序（例如 Windows PowerShell 的 Active Directory 模块或 Active Directory 管理中心）则无法访问或管理在此服务器上运行的目录服务实例。 有关详细信息，请参阅 Windows Server 技术库中 [AD DS： Active Directory Web 服务 (中的新增功能](https://technet.microsoft.com/library/dd391908\(WS.10\).aspx) https://technet.microsoft.com/library/dd391908(WS.10).aspx) 。

 **解决方法：**

##### <a name="to-start-the-active-directory-web-services-service"></a>启动 Active Directory Web Services 服务

1.  在服务器上打开 services.msc。

2.  右键单击“Active Directory Web Services”****，然后单击“启动”****。

### <a name="the-dhcp-client-service-should-be-started"></a>应启动 DHCP Client 服务
 **问题：**  DHCP 客户端服务未在服务器上运行。

 **影响：**  如果此服务已停止，则客户端计算机将无法从服务器接收 IP 地址。

 **解决方法：**

##### <a name="to-start-the-dhcp-client-service"></a>启动 DHCP Client 服务

1.  在服务器上打开 services.msc。

2.  右键单击“DHCP Client”**** 服务，然后单击“启动”****。

### <a name="the-iis-admin-service-should-be-started"></a>应启动 IIS Admin Service
 **问题：**  IIS 管理服务未在服务器上运行。

 **影响：**  如果此服务已停止，则您可能无法访问在服务器上运行的网站，如远程 Web 访问。

 **解决方法：**

##### <a name="to-start-the-iis-admin-service"></a>启动 IIS Admin Service

1.  在服务器上打开 services.msc。

2.  右键单击“IIS Admin Service”****，然后单击“启动”****。

### <a name="the-world-wide-web-publishing-service-should-be-started"></a>应启动 World Wide Web Publishing Service
 **问题：**  World Wide Web 发布服务未在服务器上运行。

 **影响：**  如果此服务已停止，则您可能无法访问在服务器上运行的网站，如远程 Web 访问。

 **解决方法：**

##### <a name="to-start-the-world-wide-web-publishing-service"></a>启动 World Wide Web Publishing Service

1.  在服务器上打开 services.msc。

2.  右键单击“World Wide Web Publishing Service”****，然后单击“启动”****。

### <a name="the-remote-desktop-gateway-service-should-be-started"></a>应启动 Remote Desktop Gateway 服务
 **问题：**  服务器上未运行远程桌面网关服务。

 **影响：**  如果此服务已停止，则用户可能无法使用远程 Web 访问访问计算机。

 **解决方法：**

##### <a name="to-start-the-remote-desktop-gateway-service"></a>启动远程桌面网关服务

1.  在服务器上打开 services.msc。

2.  右键单击“Remote Desktop Gateway”**** 服务，然后单击“启动”****。

### <a name="the-windows-time-service-should-be-started"></a>应启动 Windows Time 服务
 **问题：**  Windows 时间服务未在服务器上运行。

 **影响：**  如果此服务已停止，则数据和时间同步将不可用。

 **解决方法：**

##### <a name="to-start-the-windows-time-service"></a>启动 Windows 时间服务

1.  在服务器上打开 services.msc。

2.  右键单击“Windows Time”**** 服务，然后单击“启动”****。

### <a name="the-distributed-transaction-coordinator-msdtc-service-logon-account-should-be-nt-authoritynetwork-service"></a>Distributed Transaction Coordinator (MSDTC) 服务登录帐户应为 NT AUTHORITY\Network Service
 **问题：**  更改了分布式事务处理协调器 (MSDTC) 服务的默认登录帐户。

 **影响：**  该服务可能没有按预期方式工作所需的权限。 因此，使用 SQL Server 或 COM 功能的应用程序可能无法正常工作。

 **解决方法：**

##### <a name="to-change-the-logon-account-for-the-service"></a>更改此服务的登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击 **Distributed Transaction Coordinator** 服务，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“此帐户”****，键入“NT AUTHORITY\Network Service”****，然后单击“确定”****。

### <a name="the-netlogon-service-should-use-the-local-system-account-as-its-logon-account"></a>Netlogon 服务应使用本地系统帐户作为其登录帐户
 **问题：**  Netlogon 服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作所需的权限。 因此，服务器可能不会对用户和服务进行身份验证。

 **解决方法：**

##### <a name="to-change-the-netlogon-service-logon-account"></a>更改 Netlogon 服务登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“Netlogon”**** 服务，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“本地系统帐户”****。

### <a name="the-dns-client-service-should-use-the-nt-authoritynetwork-service-account-as-its-logon-account"></a>DNS Client 服务应使用 NT AUTHORITY\Network Service 帐户作为其登录帐户
 **问题：**  DNS 客户端服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作所需的权限。 因此，服务器可能无法解析 DNS 名称。

 **解决方法：**

##### <a name="to-change-the-dns-client-service-logon-account"></a>更改 DNS Client 服务登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“DNS Client”**** 服务，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“此帐户”****，然后键入“NT AUTHORITY\Network Service”****。

### <a name="the-dns-server-service-should-use-the-local-system-account-as-its-logon-account"></a>DNS 服务器服务应使用本地系统帐户作为其登录帐户
 **问题：**  DNS 服务器服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作所需的权限。 因此，可能无法进行 DNS 更新。

 **解决方法：**

##### <a name="to-change-the-dns-server-service-logon-account"></a>更改 DNS Server 服务登录帐户

1.  在服务器上打开 services.msc

2.  右键单击“DNS Server”**** 服务，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“本地系统帐户”****。

### <a name="active-directory-web-services-is-not-the-default-logon-account"></a>Active Directory Web Services 不是默认登录帐户
 **问题：**  Active Directory Web 服务不是默认登录帐户。 默认情况下，登录帐户设置为“本地系统帐户”****。

 **影响：**  未启动 Active Directory Web 服务 (ADWS) 。 如果服务器上的 ADWS 已停止或禁用，客户端应用程序（例如 Windows PowerShell 的 Active Directory 模块或 Active Directory 管理中心）则无法访问或管理在此服务器上运行的目录服务实例。 有关详细信息，请参阅 Windows Server 技术库中 [AD DS： Active Directory Web 服务 (中的新增功能](https://technet.microsoft.com/library/dd391908\(WS.10\).aspx) https://technet.microsoft.com/library/dd391908(WS.10).aspx) 。

 **解决方法：**

##### <a name="to-change-the-active-directory-web-services-logon-account"></a>更改 Active Directory Web Services 登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“Active Directory Web Services”****，然后单击“属性”****。

3.  将“启动类型”**** 更改为“自动”****，然后单击“确定”****。

4.  在 Active Directory Web Services“属性”**** 中，单击“登录”**** 选项卡。

5.  选择“本地系统帐户”**** 选项，然后单击“确定”****。

### <a name="the-windows-update-service-should-use-the-local-system-account-as-its-logon-account"></a>Windows Update 服务应使用本地系统帐户作为其登录帐户
 **问题：**  自动更新服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作所需的权限。 因此，服务器可能无法接收自动更新。

 **解决方法：**

##### <a name="to-change-the-windows-update-service-logon-account"></a>更改 Windows Update 服务登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“Windows Update”**** 服务，然后单击“属性”。

3.  在“登录”**** 选项卡上，选择“本地系统帐户”****。

### <a name="the-dhcp-client-service-should-use-the-nt-authoritylocalservice-account-as-its-logon-account"></a>DHCP Client 服务应使用 NT AUTHORITY\LocalService 帐户作为其登录帐户
 **问题：**  DHCP 客户端服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作所需的权限。 因此，客户端计算机将不会从服务器接收 IP 地址。

 **解决方法：**

##### <a name="to-change-the-dhcp-client-service-logon-account"></a>更改 DHCP Client 服务登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“DHCP Client”**** 服务，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“此帐户”****，然后键入“NT AUTHORITY\Local Service”****。

### <a name="the-iis-admin-service-should-use-the-local-system-account-as-its-logon-account"></a>IIS Admin Service 应使用本地系统帐户作为其登录帐户
 **问题：**  IIS 管理服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作所需的权限。 因此，你可能无法访问在服务器上运行的网站，例如“远程 Web 访问”。

 **解决方法：**

##### <a name="to-change-the-service-logon-account"></a>更改服务登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“IIS Admin Service”****，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“本地系统帐户”****。

### <a name="the-world-wide-web-publishing-service-should-use-the-local-system-account-as-its-logon-account"></a>World Wide Web Publishing Service 应使用本地系统帐户作为其登录帐户
 **问题：**  World Wide Web 发布服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作所需的权限。 因此，你可能无法访问在服务器上运行的网站，例如“远程 Web 访问”。

 **解决方法：**

##### <a name="to-change-the-world-wide-web-publishing-service-logon-account"></a>更改 World Wide Web Publishing Service 登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“World Wide Web Publishing Service”****，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“本地系统帐户”****。

### <a name="the-remote-desktop-gateway-service-should-use-the-nt-authoritynetwork-service-account-as-its-logon-account"></a>Remote Desktop Gateway 服务应使用 NT AUTHORITY\Network Service 帐户作为其登录帐户
 **问题：**  远程桌面网关服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作的适当权限。 因此，用户可能无法使用“远程 Web 访问”来访问计算机。

 **解决方法：**

##### <a name="to-change-the-remote-desktop-gateway-service-logon-account"></a>更改 Remote Desktop Gateway 服务登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“Remote Desktop Gateway”**** 服务，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“此帐户”****，然后键入“NT AUTHORITY\Network Service”****。

### <a name="the-windows-time-service-should-use-the-nt-authoritynetwork-service-account-as-its-logon-account"></a>Windows Time 服务应使用 NT AUTHORITY\Network Service 帐户作为其登录帐户
 **问题：**  Windows 时间服务的默认登录帐户已更改。

 **影响：**  该服务可能没有按预期方式工作的适当权限。 因此，日期和时间同步可能无法使用。

 **解决方法：**

##### <a name="to-change-the-windows-time-service-logon-account"></a>更改 Windows Time 服务登录帐户

1.  在服务器上打开 services.msc。

2.  右键单击“Windows Time”**** 服务，然后单击“属性”****。

3.  在“登录”**** 选项卡上，选择“此帐户”****，然后键入“NT AUTHORITY\Local Service”****。

### <a name="the-built-in-administrators-group-does-not-have-the-right-to-log-on-as-batch-job"></a>内置管理员组没有作为批处理作业登录的权限
 **问题：**  内置管理员组没有作为批处理作业登录的权限。

 **影响：**  如果管理员创建了一个警报并将该警报配置为在管理员未登录时运行，则该警报将失败并出现错误代码2147943785。

 **解决方法：**  有关如何向内置管理员组授予作为批处理作业登录的权限的信息，请参阅 [向内置管理员组提供作为批处理作业登录的](/previous-versions/orphan-topics/ws.11/jj635076(v=ws.11)) 权限 (https://technet.microsoft.com/library/jj635076) 。

### <a name="the-windows-firewall-is-turned-off"></a>Windows 防火墙已关闭
 **问题：**  Windows 防火墙已关闭。 默认值为“打开”。

 **影响：**  根据防火墙设置，Windows 防火墙会阻止某些信息通过服务器来保护服务器和网络免受恶意活动的攻击。

 **解决方法：**

##### <a name="to-turn-on-windows-firewall-on-the-server"></a>在服务器上打开 Windows 防火墙

1.  在服务器上，打开“控制面板”。

2.  在“控制面板”中，单击“系统和安全”****，然后单击“Windows 防火墙”****。

3.  在“Windows 防火墙”中，单击“打开或关闭 Windows 防火墙”****、选择“启用 Windows 防火墙”**** 选项，然后单击“确定”****。

### <a name="the-internal-network-adapter-is-not-configured-to-register-ip-address-in-dns"></a>内部网络适配器未配置为在 DNS 中注册 IP 地址
 **问题：**  内部网络适配器未配置为在 DNS 中注册其 IP 地址。

 **影响：**  如果未在 DNS 中注册内部网络适配器的 IP 地址，则可能无法使用服务器的计算机名称访问该服务器。

 **解决方法：**  验证是否已将内部网络适配器配置为在 DNS 中注册。

### <a name="dns-the-values-for-the-dns-forwardingtimeout-and-recursiontimeout-registry-key-are-identical"></a>DNS： DNS ForwardingTimeout 和 RecursionTimeout 注册表项的值相同
 **问题：**  DNS ForwardingTimeout 注册表项的值不应与 RecursionTimeout 注册表项的值相同。

 **影响：**  你可能不能按名称访问 Internet 资源。

 **解决方法：**  将 RecursionTimeout 注册表项的值设置为大于 ForwardingTimeout 项的值（位于注册表中 HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\DNS\Parameters. 的值）。

### <a name="the-forward-dns-zone-for-your-active-directory-domain-does-not-allow-secure-updates"></a>Active Directory 域的正向 DNS 区域不允许安全更新
 **问题：**  应将正向查找区域配置为仅允许安全动态更新。

 **影响：**  启用安全动态更新时，只有经过授权的用户和主机才能对记录进行更改。

 **解决方法：**

##### <a name="to-configure-the-forward-lookup-zone-for-your-active-directory-domain"></a>配置 Active Directory 域的正向查找区域

1.  在服务器上打开 dnsmgmt.msc。

2.  右键单击 Active Directory 域的正向查找区域，然后单击“属性”****。

3.  在“动态更新”**** 下拉列表中，选择“仅安全”****，然后单击“确定”****。

### <a name="the-forward-dns-zone-does-not-allow-secure-updates"></a>正向 DNS 区域不允许安全更新
 **问题：**  应将 _msdcs. * 区域的正向查找区域配置为仅允许安全动态更新。

 **影响：**  启用安全动态更新时，只有经过授权的用户和主机才能对 msdcs. * 区域中的记录进行更改。

 **解决方法：**

##### <a name="to-allow-secure-updates-in-the-_msdcs-zone"></a>允许 _msdcs zone 中的安全更新

1.  在服务器上打开 dnsmgmt.msc。

2.  右键单击 _msdcs 区域的正向查找区域，然后单击“属性”****。

3.  在“动态更新”**** 下拉列表中，选择“仅安全”****，然后单击“确定”****。

### <a name="internet-explorer-enhanced-security-configuration-is-not-enabled"></a>Internet Explorer 增强安全配置未启用
 **问题：**  Internet Explorer 增强的安全配置 (IE ESC) 当前未为 Administrators 组启用此功能。

 **影响：**  如果未对管理员组启用 Internet Explorer 增强的安全配置，您的服务器和 Internet Explorer 可能会增加通过 Web 内容和应用程序脚本发生的恶意攻击。

 **解决方法：**

##### <a name="to-enable-internet-explorer-enhanced-security-configuration"></a>启用 Internet Explorer 增强安全配置

1.  在服务器上打开“服务器管理器”****，然后单击“本地服务器”****。

2.  在“属性”**** 窗格上，将“IE 增强安全配置”**** 的设置更改为“打开”****，然后单击“确定”****。

### <a name="internet-explorer-enhanced-security-configuration-is-not-enabled"></a>Internet Explorer 增强安全配置未启用
 **问题：**  Internet Explorer 增强的安全配置 (IE ESC) 当前未为用户组启用此功能。

 **影响：**  如果未对用户组启用 Internet Explorer 增强的安全配置，您的服务器和 Internet Explorer 可能会增加通过 Web 内容和应用程序脚本发生的恶意攻击。

 **解决方法：**

##### <a name="to-enable-internet-explorer-enhanced-security-configuration"></a>启用 Internet Explorer 增强安全配置

1.  打开“服务器管理器”****，然后单击“本地服务器”****。

2.  在“属性”**** 窗格上，将“IE 增强安全配置”**** 的设置更改为“打开”****，然后单击“确定”****。

### <a name="the-source-server-remains-in-active-directory-sites-and-services"></a>源服务器将保留在“Active Directory 站点和服务”中
 **问题：**  默认情况下，运行 Windows Small Business Server 的源服务器仍存在于 Active Directory 站点和服务中。

 **影响：**  如果源服务器保留在 Active Directory 站点和服务中，则客户端计算机可能会遇到连接问题： s。

 **解决方法：**  应将源服务器降级，将其从域中删除，然后从 Active Directory 站点和服务和 Active Directory 用户和计算机中删除源服务器。

### <a name="source-server-remains-in-sbscomputer-ou"></a>源服务器保留在 SBSComputer OU 中
 **问题：**  运行 Windows Small Business Server 的源服务器仍存在于 Active Directory 用户和计算机中。

 **影响：**  如果源服务器保留在 Active Directory 用户和计算机中，则客户端计算机可能会遇到连接问题： s。

 **解决方法：**  应将源服务器降级，将其从域中删除，然后从 Active Directory 站点和服务和 Active Directory 用户和计算机中删除源服务器。

### <a name="a-group-policy-is-missing"></a>组策略缺失
 **问题：**  缺少默认域策略组策略。

 **影响：**  对于正确的域函数，默认域策略是必需的。

 **解决方法：**

##### <a name="to-restore-a-missing-group-policy"></a>还原缺失的组策略

1.  在服务器上打开 gpmc.msc。

2.  在“组策略管理器”中，展开域林，然后在控制台树中搜索“Default Domain Policy”**** 组策略对象。

3.  如果策略未出现在树中，则从系统状态备份中将其还原。

### <a name="no-dns-name-server-resource-records"></a>没有 DNS 名称服务器资源记录
 **问题：**  服务器的正向查找区域中没有 (NS) 资源记录的 DNS 名称服务器。

 **影响：**  如果 Active Directory 域的正向查找区域中不存在 DNS 名称服务器 (NS) 资源记录，则用户可能无法访问网络或 Internet 上的资源。

 **解决方法：**

##### <a name="to-restore-missing-dns-name-server-resource-records"></a>还原缺失的 DNS 名称服务器资源记录

1.  在服务器上打开 dnsmgmt.msc。

2.  在“DNS 管理器”中，右键单击 Active Directory 域的正向查找区域，然后单击“属性”****。

3.  在“名称服务器”**** 选项卡上，确认设置是否正确。

4.  进行任何必要的更改，然后单击“确定”**** 保存设置。

### <a name="no-dns-name-server-records"></a>没有 DNS 名称服务器记录
 **问题：**  服务器的 _msdcs 区域中没有 (NS) 资源记录的 DNS 名称服务器 (例如： _msdcs) 。

 **影响：**  如果 Active Directory 域的 _msdcs 区域中不存在 (NS) 资源记录的 DNS 名称服务器，则用户可能无法访问网络或 Internet 上的资源。

 **解决方法：**

##### <a name="to-restore-missing-dns-name-server-records"></a>还原缺失的 DNS 名称服务器资源记录

1.  在服务器上打开 dnsmgmt.msc。

2.  在“DNS 管理器”中，右键单击 _msdcs 区域的正向查找区域，然后单击“属性”****。

3.  在“名称服务器”**** 选项卡上，确认设置是否正确。

4.  进行任何必要的更改，然后单击“确定”**** 保存设置。

### <a name="no-dns-name-server-records"></a>没有 DNS 名称服务器记录
 **问题：**  对于委派的 _msdcs 正向查找区域，不存在 (NS) 资源记录的 DNS 名称服务器。

 **影响：**  如果委派的 _msdcs 正向查找区域中不存在 DNS 名称服务器 (NS) 资源记录，则 DNS 服务器服务将无法解析域的 DNS 资源记录，并且将无法启动。

 **解决方法：**

##### <a name="to-reconfigure-missing-dns-name-server-records"></a>重新配置缺失的 DNS 名称服务器记录

1.  在服务器上打开 dnsmgmt.msc。

2.  在“DNS 管理器”中，展开服务器名称，然后展开“正向查找区域”****。

3.  单击 Active Directory 域的正向查找区域（例如：contoso.local）。

4.  委派的 _msdcs 区域显示为灰色文件夹。 右键单击 _msdcs 区域，然后单击“属性”****。

5.  在“名称服务器”**** 选项卡上，确认设置是否正确。

6.  进行任何必要的更改，然后单击“确定”**** 保存设置。

### <a name="authenticated-users-not-a-member-of-the-pre-windows-2000-compatible-access-group"></a>Authenticated Users 不是 Pre-Windows 2000 Compatible Access 组的成员
 **问题：**  经过身份验证的用户组不是 Windows 2000 兼容访问组的成员。

 **影响：**  如果内置的 "经过身份验证的用户" 组不是 Windows 2000 兼容访问组的成员，则网络用户可能会遇到 "拒绝访问" 错误。

 **解决方法：**

##### <a name="to-add-authenticated-users-to-the-pre-windows-2000-compatible-access-group"></a>将 Authenticated Users 添加到 Pre-Windows 2000 Compatible Access 组

1.  在服务器上打开 dsa.msc。

2.  在“Builtin”**** 文件夹中，右键单击“Pre-Windows 2000 Compatible Access”****，然后单击“属性”****。

3.  单击“添加”****，键入“Authenticated Users”****，然后单击“确定”**** 两次。

### <a name="dns-client-not-configured"></a>DNS 客户端未配置
 **问题：**  DNS 客户端未配置为仅指向服务器的内部 IP 地址。

 **影响：**  如果 DNS 客户端未配置为仅指向服务器的内部 IP 地址，则 DNS 名称解析可能会失败。

 **解决方法：**

##### <a name="to-configure-dns-to-point-only-to-the-server-s-internal-ip-address"></a>将 DNS 配置为仅指向服务器的内部 IP 地址

1.  在客户端计算机中，打开网络连接的“属性”**** 页面。

2.  确保 DNS 已配置为仅指向服务器的内部 IP 地址。

### <a name="default-application-pool-value-changed"></a>默认应用程序池的值已改变
 **问题：**  DefaultAppPool 应用程序池的最大工作进程数未设置为默认值1。

 **影响：**  用户可能无法连接到 Windows Small Business Server 基于 web 的服务。

 **解决方法：**

##### <a name="to-reset-maximum-worker-processes-for-the-default-application-pool"></a>重置默认应用程序池的最大工作进程数

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器中，展开服务器名称，然后单击“应用程序池”****。

3.  在“应用程序池”**** 中，右键单击“DefaultAppPool”****，然后单击“高级设置”****。

4.  在“高级设置”**** 中，将“最大工作进程数”**** 的值更改为 1，然后单击“确定”****。

5.  关闭“高级设置”****，右键单击“DefaultAppPool”****，然后停止并重新启动应用程序池。

### <a name="application-pool-for-remote-web-access-does-not-use-the-default-account"></a>用于远程 Web 访问的应用程序池未使用默认帐户
 **问题：**  未在默认帐户下运行 RemoteAppPool 应用程序池。

 **影响：**  网络用户可能无法访问远程 Web 访问网站。

 **解决方法：**

##### <a name="to-reset-the-remote-application-pool-to-use-the-default-account"></a>将远程应用程序池重置为使用默认帐户

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器中，展开服务器名称，然后单击“应用程序池”****。

3.  在“应用程序池”**** 中，右键单击“RemoteAppPool”****，然后单击“高级设置”****。

4.  在“高级设置”**** 中，将“标识”**** 更改为“NetworkService”****，然后单击“确定”****。

5.  关闭“高级设置”****，右键单击“RemoteAppPool”****，然后停止并重新启动应用程序池。

### <a name="application-pool-for-remote-web-access-does-not-use-the-default-net-framework-version"></a>用于远程 Web 访问的应用程序池未使用默认 .NET Framework 版本
 **问题：**  RemoteAppPool 应用程序池未运行 Microsoft .NET Framework 的默认版本。

 **影响：**  网络用户可能无法访问远程 Web 访问网站。

 **解决方法：**

##### <a name="to-change-the-net-framework-version-used-by-the-remoteapppool"></a>更改 RemoteAppPool 使用的 .NET Framework 版本

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器中，展开服务器名称，然后单击“应用程序池”****。

3.  在“应用程序池”**** 中，右键单击“RemoteAppPool”****，然后单击“高级设置”****。

4.  在“高级设置”**** 中，将“.NET Framework Version”**** 更改为 v4.0，然后单击“确定”****。

5.  关闭“高级设置”****，右键单击“RemoteAppPool”****，然后停止并重新启动应用程序池。

### <a name="the-remoteaccesslog-file-is-larger-than-1-gb-in-size"></a>RemoteAccess.log 文件大于 1 GB 的大小
 **问题：**  如果 Remoteaccess 文件的大小超过 1 GB，则在系统驱动器上可能出现磁盘空间不足的错误。

 **影响：**  如果远程访问日志文件太大，则可能会导致可用空间问题： s （在驱动器 c： s 上）

 **解决方法：**  备份服务器后，可删除位于%ProgramData%\Microsoft\Windows Server\Logs\WebApps 文件夹中的 "Remoteaccess .log" 文件。

### <a name="default-web-sites-log-directory-is-over-1-gb-in-size"></a>默认网站的日志目录超过 1 GB 的大小
 **问题：**  如果默认网站的日志文件夹大小超过 1 GB，则可能会在系统驱动器上出现磁盘空间不足的错误。

 **影响：**  如果默认网站的日志文件夹太大，则可能会导致可用空间问题： s （在驱动器 C 上）：

 **解决方法：**  备份服务器并且默认网站停止时，可以删除 C:\inetpub\logs\LogFiles\W3SVC1 文件夹中的日志文件。 然后启动默认网站。

### <a name="no-binding-for-ssl-on-all-ip-addresses"></a>没有为所有 IP 地址绑定 SSL
 **问题：**  服务器上的所有 IP 地址上都没有安全套接字层 (SSL) 的绑定。

 **影响：**  如果 SSL 未绑定到服务器上的所有 IP 地址，则用户将无法使用某些网站。

 **解决方法：**

##### <a name="to-bind-ssl-to-all-ip-addresses-on-the-server"></a>将 SSL 绑定到服务器上的所有 IP 地址

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器的“连接”**** 窗格中，展开你的服务器，展开“网站”****，右键单击“Default Web Site”****，然后单击“编辑绑定”****。

3.  在“网站绑定”**** 中，单击“添加”****，然后选择以下设置：

    -   **类型**  = **https**

    -   **IP 地址**  = **全部未分配**

    -   “端口”****=443

4.  选择 SSL 证书，然后单击“确定”**** 保存更改。

### <a name="no-binding-for-ssl-on-the-default-web-site"></a>没有为默认网站绑定 SSL
 **问题：**  默认网站上没有适用于 SSL 的绑定。

 **影响：**  如果 SSL 未绑定到默认网站，则用户可能无法使用某些网站。

 **解决方法：**

##### <a name="to-bind-ssl-to-the-default-website"></a>将 SSL 绑定到默认网站

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器的“连接”**** 窗格中，展开你的服务器，展开“网站”****，右键单击“Default Web Site”****，然后单击“编辑绑定”****。

3.  在“网站绑定”**** 中，单击“添加”****，然后选择以下选项：

    -   **类型**  = **https**

    -   **IP 地址**  = **全部未分配**

    -   “端口”****=443

    > [!NOTE]
    >  对于特定 IP 地址，如果存在端口 443 的 HTTPS 绑定，请将对应该绑定的“IP 地址”**** 属性更改为“全部未分配”****。 此规则的例外情况是 IP 地址 127.0.0.1。 请勿更改 127.0.0.1 的绑定。

4.  选择 SSL 证书，然后单击“确定”**** 保存更改。

### <a name="a-certificate-expires-within-30-days"></a>证书在 30 天内到期
 **问题：**  服务器证书将在30天后过期。

 **影响：**  服务器不能使用过期的证书。 如果证书过期，用户可能无法使用“随处访问”功能。

 **解决方法：**  若要防止证书过期，请将证书续订为受信任的证书颁发机构。

### <a name="certificate-subject-does-not-match-the-name-configured-by-domain-name-wizard"></a>证书使用者与“域名”向导配置的名称不匹配
 **问题：**  证书使用者与 "域名" 向导配置的名称不匹配。

 **影响：**  如果证书使用者与 "域名" 向导配置的名称不匹配，某些网站将无法初始化。 其他站点将显示错误 "此网站的安全证书有问题。"

 **解决方法：**  若要解决此问题：，请再次运行 "设置随处访问" 向导并为证书提供正确的域名，或购买与你要使用的域名相匹配的新证书。

### <a name="one-or-more-user-accounts-have-duplicate-cn-names"></a>一个或多个用户帐户具有重复的 CN 名
 **问题：**  一个或多个用户帐户具有重复的 CN 名称： {0} 。

 **影响：**  如果用户帐户具有重复的 CN 名称，用户可能无法登录到网络。 此外，在 Active Directory 中搜索用户可能会返回错误值。

 **解决方法：**  若要解决此问题：，请确保网络用户帐户没有重复的 "CN =" 名称。 若要简化此过程，请考虑将 Active Directory 内容导出到文本文件中进行检查。 有关如何执行此操作的信息，请参阅 [使用 LDIFDE 将目录对象导入和导出到 Active Directory (知识库文章 237677) ](https://support.microsoft.com/kb/237677) (https://support.microsoft.com/kb/237677) 。

### <a name="nt-backup-is-installed"></a>安装了 NT 备份
 **问题：**  Windows NT 备份程序安装在服务器上。

 **影响：**   Windows Server Essentials 使用 Windows Server 备份。 如果还安装了 Windows NT 备份程序，则两个备份程序之间可能存在冲突。 这可能会导致 Windows Server Backup 进程失败。 冲突还可能阻止你使用备份还原服务器。

 **解决方法：** 若要解决此问题：，请从服务器卸载 NT 备份程序。

### <a name="iis-does-not-own-port-80-000080-or-port-443-0000443"></a>IIS 没有端口 80 (0.0.0.0:80) 或端口 443 (0.0.0.0:443)
 **问题：**  Internet Information Services (IIS) 不拥有端口 80 (0.0.0.0： 80) 或端口443。 这些端口当前通过其他应用程序绑定。

 **影响：**   Windows Server Essentials web 应用程序要求使用端口80和端口443向用户提供服务。 如果其他进程或应用程序已在使用端口80或端口443，则 Windows Server Essentials web 应用程序将无法运行。 如果发生这种情况，用户将无法使用“远程 Web 访问”及其他应用程序。

 **解决方法：**  若要解决此问题：，请卸载已在使用端口80或端口443的应用程序，或者将该应用程序分配到其他端口。

### <a name="the-default-website-is-not-running"></a>默认网站未运行
 **问题：**  默认网站未在 Windows Server Essentials 环境中运行。

 **影响：**   Windows Server Essentials web 应用程序需要使用默认网站。 如果默认网站未运行，用户将无法使用“远程 Web 访问”及其他应用程序。

 **解决方法：**

##### <a name="to-start-the-default-website"></a>启动默认网站

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器中，展开服务器名称，然后单击“网站”****。

3.  右键单击“Default Web Site”****，指向“管理网站”****，然后单击“启动”****。

### <a name="read-and-script-permissions-for-the-remote-virtual-directory-are-incorrect"></a>/Remote 虚拟目录的“读取”和“脚本”权限不正确
 **问题：**  不会为/Remote 虚拟目录分配 "读取" 和 "编写脚本" 权限。

 **影响：**  如果/Remote 虚拟目录的 "读取" 和 "脚本" 权限不正确，则用户无法使用远程 Web 访问。 当他们尝试使用远程 Web 访问浏览 Internet 时，它们可能会遇到错误 "HTTP 错误403.1 禁止访问"。

 **解决方法：**

##### <a name="to-assign-read-and-script-permissions-to-the-remote-directory"></a>为 /Remote 目录分配“读取”和“脚本”权限

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器中，展开服务器名称，然后单击“网站”****。

3.  展开“Default Web Site”****，然后展开“远程”****。

4.  在“功能视图”**** 中，双击“处理程序映射”****。

5.  在“操作”**** 窗格中，单击“编辑功能权限”****。

6.  选中“读取”**** 和“脚本”**** 复选框，然后单击“确定”****。

### <a name="http-redirect-is-either-set-or-inherited-on-the-remote-virtual-directory"></a>在 /Remote 虚拟目录上设置或继承了“HTTP 重定向”
 **问题：**  在/Remote 虚拟目录上意外设置或继承了 HTTP 重定向属性。

 **影响：**  如果在/Remote 虚拟目录上设置了 "HTTP 重定向" 属性，则远程 Web 工作区将不能正常工作。

 **解决方法：**

##### <a name="to-remove-the-http-redirect-attribute"></a>删除“HTTP 重定向”属性

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器中，展开服务器名称，然后单击“网站”****。

3.  展开“Default Web Site”****，然后展开“远程”****。

4.  在“功能视图”**** 中，双击“HTTP 重定向”****。

5.  清除“将请求重定向到此目标”**** 复选框，然后在“操作”**** 窗格中单击“应用”****。

### <a name="a-host-name-exists-for-port-80-on-the-default-website"></a>默认网站上的端口 80 存在主机名
 **问题：**  为默认网站上的端口80分配主机名。

 **影响：**  如果为默认网站上的端口80分配了主机名，则可能无法连接到某些 Windows Server Essentials web 应用程序。 在这种情况下，不需要且不建议使用主机名。

 **解决方法：**

##### <a name="to-clear-the-host-name-entry-for-port-80-on-the-default-website"></a>清除默认网站上的端口 80 的主机名条目

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器中，展开服务器名称，然后单击“网站”****。

3.  在“功能视图”**** 中，右键单击“Default Web Site”****，然后单击“绑定”****。

4.  在“网站绑定”**** 中，选择“端口 80 HTTP”**** 设置，然后单击“编辑”****。

5.  在“编辑网站绑定”**** 中，清除“主机名”**** 条目，然后单击“确定”****。

### <a name="backup-does-not-succeed-because-of-a-hidden-partition"></a>由于隐藏分区，备份失败
 **问题：**  Windows Server 备份将非 NTFS 分区计划为备份。

 **影响：**  Windows Server 备份只能备份格式化为 NTFS 的分区。

 **解决方法：**  不要将 Windows Server 备份配置为备份非 NTFS 分区。 有关详细信息，请参阅 [Windows Server 2008 计算机上的系统状态备份失败时记录的事件 id 12290 和 16387 (知识库文章 968128) ](https://support.microsoft.com/kb/968128) (https://support.microsoft.com/kb/968128) 。

### <a name="the-most-recent-backup-did-not-succeed"></a>最新备份失败
 **问题：**  最近的备份尝试未成功完成。

 **影响：**  系统的备份状态不正确。

 **解决方法：**  查看事件日志和备份日志，以了解在最近的备份过程中发生的错误。

### <a name="the-startup-type-for-the-file-replication-service-is-not-set-to-automatic"></a>File Replication Service 的启动类型未设置为“自动”
 **问题：**  如果启动类型未设置为 "自动" 的默认值，则文件复制服务 (FRS) 可能无法启动。

 **影响：**  如果文件复制服务未运行，域控制器可能会停止播发其服务。 这可能会导致其他问题，例如登录错误和组策略错误。

 **解决方法：**

##### <a name="to-configure-the-file-replication-service-for-automatic-startup"></a>将 File Replication Service 配置为自动启动

1.  打开“服务”控制台。

2.  在服务列表中，双击“File Replication”****。

3.  对于“启动类型”****，选择“自动”****，然后单击“应用”****。

### <a name="the-file-replication-service-is-not-running"></a>File Replication Service 未运行
 **问题：**  文件复制服务未运行。

 **影响：**  如果文件复制服务未运行，域控制器可能会停止播发其服务。 此行为可能导致其他问题，例如登录错误和组策略错误。

 **解决方法：**

##### <a name="to-start-the-file-replication-service"></a>启动 File Replication Service

1.  打开“服务”控制台。

2.  在服务列表中，双击“File Replication Service”****。

3.  单击“启动”。

### <a name="the-logon-account-for-the-file-replication-service-is-not-set-to-use-the-local-system-account"></a>File Replication Service 的登录帐户未设置为使用“本地系统帐户”
 **问题：**  文件复制服务未配置为使用本地系统帐户作为默认登录帐户。

 **影响：**  如果文件复制服务未将 "本地系统" 用作默认登录帐户，你可能会遇到与权限相关的错误。 这些错误可能触发其他错误，并可能最终导致域控制器停止播发其服务。

 **解决方法：**

##### <a name="to-configure-local-system-as-the-default-logon-account-for-file-replication"></a>将“本地系统”配置为 File Replication 的默认登录帐户

1.  打开“服务”控制台。

2.  在服务列表中，双击“File Replication”****。

3.  在“服务属性”**** 页上，单击“登录”**** 选项卡。

4.  选择“本地系统帐户”**** 选项，然后单击“应用”****。

5.  重启服务。

### <a name="the-startup-type-for-the-dfs-replication-service-is-not-set-to-automatic"></a>DFS Replication 服务的启动类型未设置为“自动”
 **问题：**  如果启动类型未设置为默认值 "自动"，则 DFS 复制服务可能无法启动。

 **影响：**  如果 DFS 复制服务未运行，域控制器可能会停止播发其服务。 这可能会导致其他问题，例如登录错误和组策略错误。

 **解决方法：**

##### <a name="to-configure-the-dfs-replication-service-for-automatic-startup"></a>将 DFS Replication 服务配置为自动启动

1.  打开“服务”控制台。

2.  在服务列表中，双击“DFS Replication”****。

3.  对于“启动类型”****，选择“自动”****，然后单击“应用”****。

### <a name="the-dfs-replication-service-is-not-running"></a>DFS Replication 服务未运行
 **问题：**  DFS 复制服务当前未运行。

 **影响：**  如果 DFS 复制服务未运行，域控制器可能会停止播发其服务。 此行为可能导致其他问题，例如登录错误和组策略错误。

 **解决方法：**

##### <a name="to-start-the-dfs-replication-service"></a>启动 DFS Replication 服务

1.  打开“服务”控制台。

2.  在服务列表中，双击“DFS Replication”****。

3.  单击“启动”。

### <a name="the-dfs-replication-service-is-not-is-not-set-to-use-the-local-system-account"></a>DFS Replication 服务未设置为使用“本地系统帐户”
 **问题：**  DFS 复制服务未设置为使用本地系统帐户作为默认登录帐户。

 **影响：**  如果 DFS 复制服务不将 "本地系统" 用作默认登录帐户，你可能会遇到与权限相关的错误。 这些错误可能触发其他错误，并可能最终导致域控制器停止播发其服务。

 **解决方法：**

##### <a name="to-configure-dfs-replication-to-use-local-system-as-the-default-logon-account"></a>将 DFS Replication 配置为使用“本地系统”作为默认登录帐户

1.  打开“服务”控制台。

2.  在服务列表中，双击“DFS Replication”****。

3.  在“服务属性”**** 页上，单击“登录”**** 选项卡。

4.  选择“本地系统帐户”**** 选项，然后单击“应用”****。

5.  重启服务。

### <a name="the-windows-server-microsoft-365-integration-service-is-not-set-to-use-the-local-system-account"></a>Windows Server Microsoft 365 Integration Service 未设置为使用本地系统帐户
 **问题：**  Windows Server Microsoft 365 Integration Service 未设置为使用本地系统帐户作为默认登录帐户。

 **影响：**  如果 Windows Server Microsoft 365 Integration Service 未将 "本地系统" 用作默认登录帐户，则 Microsoft 365 的某些功能可能无法正常工作。 你可能还会遇到与权限相关的错误。

 **解决方法：**

##### <a name="to-configure-the-microsoft-365-integration-service-to-use-local-system-as-the-default-logon-account"></a>将 Microsoft 365 Integration Service 配置为使用 "本地系统" 作为默认登录帐户

1.  打开“服务”控制台。

2.  在服务列表中，双击 " **Windows Server Microsoft 365 Integration Service**"。

3.  在“服务属性”**** 页上，单击“登录”**** 选项卡。

4.  选择“本地系统帐户”**** 选项，然后单击“应用”****。

5.  重启服务。

### <a name="the-windows-server-microsoft-365-integration-service-is-not-running"></a>Windows Server Microsoft 365 Integration Service 未运行
 **问题：**  Windows Server Microsoft 365 Integration Service 当前未运行。

 **影响：**  如果 Windows Server Microsoft 365 Integration Service 未运行，则 Microsoft 365 的基于云的功能不可用。

 **解决方法：**

##### <a name="to-start-the-windows-server-microsoft-365-integration-service"></a>启动 Windows Server Microsoft 365 Integration Service

1.  打开“服务”控制台。

2.  在服务列表中，双击 " **Windows Server Microsoft 365 Integration Service**"。

3.  单击“启动”。

### <a name="the-startup-type-for-the-windows-server-microsoft-365-integration-service-is-not-set-to-automatic"></a>Windows Server Microsoft 365 Integration Service 的启动类型未设置为 "自动"
 **问题：**  如果启动类型未设置为默认值 "自动"，则 Windows Server Microsoft 365 Integration Service 可能无法启动。

 **影响：**  如果 Windows Server Microsoft 365 Integration Service 未运行，则 Microsoft 365 的基于云的功能不可用。

 **解决方法：**

##### <a name="to-configure-the-microsoft-365-integration-service-for-automatic-startup"></a>将 Microsoft 365 Integration Service 配置为自动启动

1.  打开“服务”控制台。

2.  在服务列表中，双击 " **Windows Server Microsoft 365 Integration Service**"。

3.  对于“启动类型”****，选择“自动”****，然后单击“应用”****。

### <a name="a-registry-value-is-missing-or-set-incorrectly"></a>注册表值缺失或设置错误
 **问题：**  HKEY_LOCAL_MACHINE \Software\Microsoft\Rpc\RpcProxy 下的注册表项包含不正确的值，或不存在。

 **影响：**  如果 RPCProxy 注册表项设置不正确，可能会收到类似于以下内容的错误消息： "您的计算机无法连接到远程计算机，因为远程桌面网关服务器暂时不可用。 请稍后尝试重新连接，或与网络管理员联系以获取帮助。”

 **解决方法：**

##### <a name="to-correct-the-registry-setting"></a>更正注册表设置

1.  打开注册表编辑器。

2.  导航到以下注册表项：

     HKEY_LOCAL_MACHINE\Software\Microsoft\Rpc\RpcProxy

3.  确保名为 "网站" 的字符串具有默认网站的数据值：

    -   如果数据值不正确，请修改该字符串以使用正确值。

    -   如果该字符串不存在，请创建一个名为 "网站" 的新字符串，并将数据值设置为 "默认网站"。

### <a name="the-startup-type-for-the-block-level-backup-engine-service-is-not-set-to-manual"></a>Block Level Backup Engine Service 的启动类型未设置为“手动”
 **问题：**  块级备份引擎服务未使用默认的启动类型 "手动"。

 **影响：**  如果 "启动类型" 未设置为 "手动"，则块级备份引擎服务可能无法启动。 此问题：可能会导致 Windows Server 备份作业失败。

 **解决方法：**

##### <a name="to-configure-the-block-level-backup-engine-service-for-manual-startup"></a>将 Block Level Backup Engine Service 配置为手动启动

1.  打开“服务”控制台。

2.  在服务列表中，双击“Block Level Backup Engine Service”****。

3.  对于“启动类型”****，选择“手动”****，然后单击“应用”****。

### <a name="the-logon-account-for-the-block-level-backup-engine-service-is-not-set-to-use-the-local-system-account"></a>Block Level Backup Engine Service 的登录帐户未设置为使用“本地系统帐户”
 **问题：**  块级备份引擎服务未设置为使用本地系统帐户作为默认登录帐户。

 **影响：**  如果块级备份引擎服务未将 "本地系统" 用作默认登录帐户，你可能会遇到与权限相关的错误。 这些错误可能会导致 Windows Server Backup 作业无法成功完成。

 **解决方法：**

##### <a name="to-configure-the-block-level-backup-engine-service-to-use-local-system-as-the-default-logon-account"></a>将 Block Level Backup Engine Service 配置为使用“本地系统”作为默认登录帐户

1.  打开“服务”控制台。

2.  在服务列表中，双击“Block Level Backup Engine Service”****。

3.  在“服务属性”**** 页上，单击“登录”**** 选项卡。

4.  选择“本地系统帐户”**** 选项，然后单击“应用”****。

5.  重启服务。

### <a name="the-common-name-on-the-certificate-that-is-bound-to-the-wss-certificate-web-service-website-does-not-match-the-server-name"></a>绑定到 WSS Certificate Web Service 网站的证书上的公用名与服务器名称不匹配
 **问题：**  一个无效证书绑定到 IIS 中的 WSS 证书 Web 服务网站。 此证书上的公用名与服务器名称不匹配。

 **影响：**  如果将无效证书绑定到 WSS 证书 Web 服务网站，则连接向导可能无法正常工作。

 **解决方法：**

##### <a name="to-configure-a-valid-certificate-for-the-wss-certificate-web-service"></a>为 WSS Certificate Web Service 配置有效证书

1.  在服务器上打开“Internet 信息服务 (IIS) 管理器”。

2.  在 IIS 管理器中，展开服务器名称，然后单击“网站”****。

3.  右键单击“WSS Certificate Web Service”****，然后单击“编辑绑定”****。

4.  在“网站绑定”**** 中，单击“HTTPS”****，然后单击“编辑”****。

5.  在“编辑网站绑定”**** 中，对于“SSL 证书”****，选择与你的服务器名称相同的证书。

6.  如果多个证书条目的名称都与服务器名称相同，请单击“查看”**** 确定哪个证书是有效证书，然后选择适当的证书。

### <a name="there-appears-to-be-a-problem-with-the-certificate-binding-for-the-remote-desktop-gateway-service"></a>Remote Desktop Gateway 服务的证书绑定似乎出现问题
 **问题：**  远程桌面网关服务的证书似乎绑定不正确。

 **影响：**  如果远程桌面网关服务的证书配置不正确，则用户无法连接到远程 Web 访问。

 **解决方法：**

##### <a name="to-fix-the-binding-for-the-remote-desktop-gateway-service"></a>修复 Remote Desktop Gateway 服务的绑定

-   以管理员身份打开命令提示符，然后输入以下命令：

    ```
    REG ADD HKLM\SYSTEM\CurrentControlSet\services\HTTP\Parameters\SslBindingInfo\0.0.0.0:443  /v DefaultFlags /t REG_DWORD /d 1 /f
    net stop tsgateway
    net start tsgateway
    ```

     有关详细信息，请参阅 [如何在 Windows Server Essentials 中管理远程桌面网关服务 (知识库文章 2472211) ](https://support.microsoft.com/kb/2472211) (https://support.microsoft.com/kb/2472211) 。