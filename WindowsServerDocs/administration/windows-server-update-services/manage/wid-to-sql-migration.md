---
title: 将 WSUS 数据库从 (Windows 内部数据库) WID 迁移到 SQL
description: Windows Server Update 服务 (WSUS) 主题-如何将 WSUS 数据库 (SUSDB) 从 Windows 内部数据库实例迁移到 SQL Server 的本地或远程实例。
ms.topic: get-started article
ms.assetid: 90e3464c-49d8-4861-96db-ee6f8a09g7dr
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/25/2018
ms.openlocfilehash: 54f7eb0464d4454bd2929aace44eb37567973154
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624463"
---
# <a name="migrating-the-wsus-database-from-wid-to-sql"></a>将 WSUS 数据库从 WID 迁移到 SQL

> 适用于： Windows Server 2012、Windows Server 2012 R2、Windows Server 2016

使用以下步骤将 WSUS 数据库 (SUSDB) 从 Windows 内部数据库实例迁移到 SQL Server 的本地或远程实例。

## <a name="prerequisites"></a>先决条件

- SQL 实例。 这可以是默认的 **MSSQLServer** 或自定义实例。
- SQL Server Management Studio
- 已安装 WID 角色的 WSUS
- IIS (通过服务器管理器) 安装 WSUS 时，通常会包括此步骤。 它尚未安装，将需要。

## <a name="migrating-the-wsus-database"></a>迁移 WSUS 数据库

### <a name="stop-the-iis-and-wsus-services-on-the-wsus-server"></a>在 WSUS 服务器上停止 IIS 和 WSUS 服务

从 PowerShell (提升的) 中，运行：

```powershell
    Stop-Service IISADMIN
    Stop-Service WsusService
```

### <a name="detach-susdb-from-the-windows-internal-database"></a>从 Windows 内部数据库分离 SUSDB

#### <a name="using-sql-management-studio"></a>使用 SQL Management Studio

1. 右键单击 " **SUSDB** - &gt; **任务** - &gt; "，单击 "**分离**： ![ image1](images/image1.png)
2. 选中 " **删除现有连接** "，然后单击 **"确定"** (可选，如果) 存在活动的连接。
    ![image2](images/image2.png)

#### <a name="using-command-prompt"></a>使用命令提示符

> [!IMPORTANT]
> 以下步骤演示了如何使用 **sqlcmd** 实用工具从 Windows 内部数据库实例分离 WSUS 数据库 (SUSDB) 。 有关 **sqlcmd** 实用工具的详细信息，请参阅 [sqlcmd 实用工具](https://go.microsoft.com/fwlink/?LinkId=81183)。
> 1. 打开提升的命令提示符
> 2. 运行以下 SQL 命令，通过 **sqlcmd** 实用工具从 Windows 内部数据库实例分离 WSUS 数据库 (SUSDB) ：

```batchfile
        sqlcmd -S \\.\pipe\Microsoft##WID\tsql\query
        use master
        GO
        alter database SUSDB set single_user with rollback immediate
        GO
        sp_detach_db SUSDB
        GO
```

### <a name="copy-the-susdb-files-to-the-sql-server"></a>将 SUSDB 文件复制到 SQL Server

1. 将**SUSDB**和 SUSDB 文件**从 \_ ** wid data 文件夹复制 (**% SystemDrive%** \\ **Windows \\ WID \\ data**) 到 SQL 实例数据文件夹。

> [!TIP]
> 例如，如果 SQL 实例文件夹是 **C:\Program FILES\MICROSOFT sql Server\MSSQL12。MSSQLSERVER\MSSQL**，WID Data 文件夹为 **C:\Windows\WID\Data，** 将 SUSDB 文件从 **C:\Windows\WID\Data** 复制到 **C:\Program Files\Microsoft SQL Server\MSSQL12。MSSQLSERVER\MSSQL\Data**

### <a name="attach-susdb-to-the-sql-instance"></a>将 SUSDB 附加到 SQL 实例

1. 在 **SQL Server Management Studio**的 " **实例** " 节点下，右键单击 " **数据库**"，然后单击 " **附加**"。
    ![image3](images/image3.png)
2. 在 " **附加数据库** " 框中的 " **要附加的数据库**" 下，单击 " **添加** " 按钮，然后找到 **SUSDB** 文件 (从 WID 文件夹复制) ，然后单击 **"确定"**。
    ![image4.jpg ](images/image4.png) ![ image5](images/image5.png)

> [!TIP]
> 也可以使用 Transact-sql 来完成此操作。  有关附加数据库的说明，请参阅 [SQL 文档](/sql/relational-databases/databases/attach-a-database) 。
>
> 使用前面示例中的路径 (示例) ：
> ```sql
>    USE master;
>    GO
>    CREATE DATABASE SUSDB
>    ON
>        (FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Data\SUSDB.mdf'),
>        (FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SUSDB_Log.ldf')
>        FOR ATTACH;
>    GO
>```

### <a name="verify-sql-server-and-database-logins-and-permissions"></a>验证 SQL Server 和数据库登录名和权限

#### <a name="sql-server-login-permissions"></a>SQL Server 登录权限

附加 SUSDB 后，通过执行以下操作，验证 **NT AUTHORITY\NETWORK 服务** 是否具有对 SQL Server 实例的登录权限：

1. 进入 SQL Server Management Studio
2. 打开实例
3. 单击 "**安全**"
4. 单击 "**登录**"

应该列出 **NT AUTHORITY\NETWORK SERVICE** 帐户。 如果不是，则需要通过添加新的登录名来添加它。

> [!IMPORTANT]
> 如果 SQL 实例与 WSUS 在不同的计算机上，则应以 **[FQDN] \\ [WSUSComputerName] $** 格式列出 WSUS 服务器的计算机帐户。  否则，可以使用以下步骤添加它，将**NT AUTHORITY\NETWORK SERVICE**替换为 WSUS 服务器的计算机帐户 (**[FQDN] \\ [WSUSComputerName] $**) 此操作***除了***授予**NT AUTHORITY\NETWORK 服务**的权限

##### <a name="adding-nt-authoritynetwork-service-and-granting-it-rights"></a>添加 NT AUTHORITY\NETWORK SERVICE 并向其授予权限

1. 右键单击 "**登录名**"，然后单击 "**新建登录名 ...** "
    ![图片6](images/image6.png)
2. 在 "**常规**" 页上， (**NT AUTHORITY\NETWORK SERVICE**) 中填写**登录名**，并将**默认数据库**设置为 SUSDB。
    ![image7](images/image7.png)
3. 在 " **服务器角色** " 页上，确保选择 " **公用** " 和 " **sysadmin** "。
    ![image8](images/image8.png)
4. 在 " **用户映射** " 页上：
    - 在 " **映射到此登录名的用户**" 下：选择 **SUSDB**
    - 在 " **数据库角色成员身份： SUSDB**" 下，确保选中以下内容：
        - **public**
        - **webService** ![image9](images/image9.png)
5. 单击 **“确定”**

你现在应在 "登录名" 下看到 **NT AUTHORITY\NETWORK 服务** 。
![image10](images/image10.png)

#### <a name="database-permissions"></a>数据库权限

1. 右键单击 SUSDB
2. 选择“属性”
3. 单击 **权限**

应该列出 **NT AUTHORITY\NETWORK SERVICE** 帐户。

1. 如果不是，请添加帐户。
2. 在 "登录名" 文本框中，按以下格式输入 WSUS 计算机：
    > [**FQDN] \\[WSUSComputerName] $**
3. 验证 " **默认数据库** " 是否设置为 " **SUSDB**"。

    > [!TIP]
    > 在以下示例中，FQDN 为 **Contosto.com** ，WSUS 计算机名称为 **WsusMachine**：
    >
    > ![image11](images/image11.png)

4. 在 "**用户映射**" 页上，选择 "**映射到此登录名的用户**" 下的**SUSDB**数据库。
5. 在**数据库角色成员资格**下检查**webservice** ： SUSDB： ![ image12](images/image12.png)
6. 单击  **"确定"** 保存设置。
    > [!NOTE]
    > 可能需要重新启动 SQL 服务，更改才能生效。

### <a name="edit-the-registry-to-point-wsus-to-the-sql-server-instance"></a>编辑注册表以将 WSUS 指向 SQL Server 实例

> [!IMPORTANT]
> 请认真遵循本部分所述的步骤。 如果注册表修改不正确，可能会发生严重问题。 在修改注册表之前，请[备份注册表](https://support.microsoft.com/help/322756)，以便在出现问题时可以还原。

1. 单击“**开始**”，再单击“**运行**”，键入“**regedit&** ”，然后单击“**确定**”。
2. 找到以下注册表项： **HKEY_LOCAL_MACHINE \software\microsoft\updateservices\server\setup\sqlservername**
3. 在 " **值** " 文本框中，键入 **[ServerName] \\ [InstanceName]**，然后单击 **"确定"**。 如果实例名称是默认实例，则键入 **[ServerName]**。
4. 找到以下注册表项： **HKEY_LOCAL_MACHINE \Software\microsoft\update Services\Server\Setup\Installed Role Services\UpdateServices-WidDatabase** ![ image13](images/image13.png)
5. 将密钥重命名为 **updateservices-api-Database** ![ image41](images/image14.png)

    > [!NOTE]
    > 如果不更新此密钥， **wsusutil.exe** 将尝试为 WID 而不是已迁移到的 SQL 实例服务。

### <a name="start-the-iis-and-wsus-services-on-the-wsus-server"></a>在 WSUS 服务器上启动 IIS 和 WSUS 服务

从 PowerShell (提升的) 中，运行：

```powershell
    Start-Service IISADMIN
    Start-Service WsusService
```

> [!NOTE]
> 如果你使用的是 WSUS 控制台，请关闭并重新启动它。

## <a name="uninstalling-the-wid-role-not-recommended"></a>不建议卸载 WID 角色 () 

> [!WARNING]
> 删除 WID 角色还会删除 (**%SystemDrive%\Program Files\Update Services\Database**) 的数据库文件夹，其中包含 WSUSUtil.exe 进行安装后任务所需的脚本。 如果选择卸载 WID 角色，请确保事先备份 **%SystemDrive%\Program Files\Update Services\Database** 文件夹。

使用 PowerShell：

```powershell
Uninstall-WindowsFeature -Name 'Windows-Internal-Database'
```

删除 WID 角色后，验证是否存在以下注册表项： **HKEY_LOCAL_MACHINE \Software\microsoft\update Services\Server\Setup\Installed role Services\UpdateServices-Database**