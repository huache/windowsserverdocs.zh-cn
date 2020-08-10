---
title: DFS 复制概述
ms.date: 03/08/2019
author: JasonGerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: 6a68d27ec7c1d06e070d18362de68e12ecbf9578
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87950751"
---
# <a name="dfs-replication-overview"></a>DFS 复制概述

> 适用于：Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008、Windows Server（半年频道）

DFS 复制是 Windows Server 中的角色服务，可让你有效地在多个服务器和站点上复制文件夹（包括那些由 DFS 命名空间路径引用的文件夹）。 DFS 复制是一种有效的多主机复制引擎，可用于保持有限带宽网络连接上服务器之间的文件夹同步。 它将文件复制服务 (FRS) 替换为用于 DFS 命名空间以及用于复制域（使用 Windows Server 2008 或更高版本域功能级别）中的 Active Directory 域服务 (AD DS) SYSVOL 文件夹的复制引擎。

DFS 复制使用一种称为远程差分压缩 (RDC) 的压缩算法。 RDC 检测文件中的数据更改，并使 DFS 复制仅复制已更改文件块而非整个文件。

有关使用 DFS 复制对 SYSVOL 进行复制的详细信息，请参阅[将 SYSVOL 复制迁移到 DFS 复制](migrate-sysvol-to-dfsr.md)。

若要使用 DFS 复制，必须创建复制组并将已复制文件夹添加到组。 下图中说明了复制组、已复制文件夹和成员。

![每个包含两个成员之间的连接的复制组都有几个已复制文件夹](media/dfsr-overview.gif)

此图所示复制组是一组称为“成员”的服务器，它参与一个或多个已复制文件夹的复制。 已复制文件夹是在每个成员上保持同步的文件夹。 图中有两个已复制文件夹：Projects 和 Proposals。 每个已复制文件夹中的数据更改时，将通过复制组成员之间的连接复制更改。 所有成员之间的连接构成复制拓扑。
如果在一个复制组中创建多个已复制文件夹，可以简化部署已复制文件夹的过程，因为该复制组的拓扑、计划和带宽限制将应用于每个已复制文件夹。 若要部署其他已复制文件夹，可以使用 Dfsradmin.exe 或按照向导中的说明来定义新的已复制文件夹的本地路径和权限。

每个已复制文件夹具有唯一的设置，例如文件和子文件夹筛选器，以便可以为每个已复制文件夹筛选出不同的文件和子文件夹。

存储在每个成员上的已复制文件夹可以位于成员中的不同卷上，已复制文件夹不必是共享文件夹也不必是命名空间的一部分。 但是，通过 DFS 管理管理单元，可以轻松共享已复制文件夹，并选择性地将其发布到现有命名空间中。

可以使用 DFS 管理、DfsrAdmin 和 Dfsrdiag 命令或调用 WMI 的脚本管理 DFS 复制。

## <a name="requirements"></a>要求

部署 DFS 复制之前，必须先按照如下所述配置服务器：

- 更新 Active Directory 域服务 (AD DS) 架构以包括 Windows Server 2003 R2 或更高版本架构附加功能。 不能对 Windows Server 2003 R2 或较旧版本架构添加项使用只读复制文件夹。
- 确保复制组中的所有服务器位于同一林中。 不能跨不同林中的服务器进行复制。
- 在用作复制组成员的所有服务器上安装 DFS 复制。
- 请与防病毒软件供应商联系，以检查你的防病毒软件是否与 DFS 复制兼容。
- 查找任何你想要在用 NTFS 文件系统格式化的卷上复制的文件夹。 DFS 复制不支持弹性文件系统 (ReFS) 或 FAT 文件系统。 DFS 复制也不支持存储在群集共享卷上的复制内容。

## <a name="interoperability-with-azure-virtual-machines"></a>Azure 虚拟机的互操作性

在 Azure 中的虚拟机上使用 DFS 复制已使用 Windows Server 进行了测试；但是，有一些必须遵循的限制和要求。

- 使用快照或已保存状态还原运行 DFS 复制的服务器以便复制 SYSVOL 文件夹之外的任何内容会导致 DFS 复制失败，这需要特殊的数据库恢复步骤。 同样，不要导出、克隆或复制虚拟机。 有关详细信息，请参阅 Microsoft 知识库中的文章 [2517913](https://support.microsoft.com/kb/2517913) 以及 [安全地虚拟化 DFSR](https://techcommunity.microsoft.com/t5/storage-at-microsoft/safely-virtualizing-dfsr/ba-p/424671)。
- 在虚拟机中承载的已复制文件夹中备份数据时，必须从来宾虚拟机中使用备份软件。
- DFS 复制需要访问物理或虚拟化域控制器 - 它不能直接与 Azure AD 通信。
- DFS 复制需要在本地复制组成员与 Azure VM 中托管的任何成员之间建立 VPN 连接。 还需配置本地路由器（例如 Forefront 威胁管理网关），允许 RPC 终结点映射程序（端口 135）和随机分配的端口（介于 49152 与 65535 之间）通过 VPN 连接进行传递。 可以使用 Set-DfsrMachineConfiguration cmdlet 或 Dfsrdiag 命令行工具指定静态端口而不是随机端口。 有关如何为 DFS 复制指定静态端口的详细信息，请参阅 [Set-DfsrServiceConfiguration](/powershell/module/dfsr/set-dfsrserviceconfiguration)。 有关为管理 Windows Server 而打开的相关端口的信息，请参阅 Microsoft 知识库中的文章 [832017](https://support.microsoft.com/kb/832017) 。

若要了解如何开始使用 Azure 虚拟机，请访问 [Microsoft Azure 网站](/azure/virtual-machines/)。

## <a name="installing-dfs-replication"></a>安装 DFS 复制

DFS 复制是文件和存储服务角色的一部分。 DFS 的管理工具（DFS 管理、Windows PowerShell 的 DFS 复制模块及命令行工具）分别安装为远程服务器管理工具的一部分。

使用 [Windows Admin Center](../../manage/windows-admin-center/overview.md)、服务器管理器或 PowerShell 安装 DFS 复制，具体如后续部分所述。

### <a name="to-install-dfs-by-using-server-manager"></a>使用服务器管理器安装 DFS 的步骤

1. 打开服务器管理器，单击 **“管理”** ，然后单击 **“添加角色和功能”** 。 将出现“添加角色和功能向导”。

2. 在 **“服务器选择”** 页面上，选择你想要在其上安装 DFS 的脱机虚拟机的服务器或虚拟硬盘 (VHD)。

3. 选择要安装的角色服务和功能。

    - 若要安装 DFS 复制服务，在“服务器角色”页上，选择“DFS 复制” 。

    - 若只安装 DFS 管理工具，请在 **“功能”** 页上，展开 **“远程服务器管理工具”** 、 **“角色管理工具”** 、 **“文件服务工具”** ，然后选择 **“DFS 管理工具”** 。

         “DFS 管理工具”安装 DFS 管理管理单元、Windows PowerShell 的 DFS 复制和 DFS 命名空间模块以及命令行工具，但它不在服务器上安装任何 DFS 服务。

### <a name="to-install-dfs-replication-by-using-windows-powershell"></a>使用 Windows PowerShell 安装 DFS 复制的步骤

使用提升的用户权限打开 Windows PowerShell 会话，然后键入以下命令，其中 <name\> 是你想要安装的角色服务或功能（请参阅下表获取一列相关角色服务或功能名称）：

```PowerShell
Install-WindowsFeature <name>
```

|角色服务或功能|名称|
|---|---|
|DFS 复制|`FS-DFS-Replication`|
|DFS 管理工具|`RSAT-DFS-Mgmt-Con`|

例如，若要安装远程服务器管理工具功能中的分布式文件系统工具部分，请键入：

```PowerShell
Install-WindowsFeature "RSAT-DFS-Mgmt-Con"
```

若要安装 DFS 复制和远程服务器管理工具功能中的分布式文件系统工具部分，请键入：

```PowerShell
Install-WindowsFeature "FS-DFS-Replication", "RSAT-DFS-Mgmt-Con"
```

## <a name="additional-references"></a>其他参考

- [DFS 命名空间和 DFS 复制概述](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj127250(v%3dws.11))
- [清单：部署 DFS 复制](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc772201(v%3dws.11))
- [清单：管理 DFS 复制](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755035(v%3dws.11))
- [部署 DFS 复制](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc770925(v%3dws.11))
- [管理 DFS 复制](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc770925(v%3dws.11))
- [对 DFS 复制进行故障排除](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc732802(v%3dws.11))
