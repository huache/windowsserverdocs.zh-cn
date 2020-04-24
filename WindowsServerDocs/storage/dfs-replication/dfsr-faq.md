---
title: DFS 复制 - 常见问题 (FAQ)
ms.date: 06/18/2014
ms.prod: windows-server
ms.technology: storage
author: JasonGerend
manager: elizapo
ms.author: jgerend
ms.openlocfilehash: 1e11f6c596d7e5eb0bdf379adcf47d21e74e9f6b
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "80815620"
---
# <a name="dfs-replication-frequently-asked-questions-faq"></a>DFS 复制：常见问题 (FAQ)


更新日期：2019 年 4 月 30 日

适用于：Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

此常见问题解答回答了有关 Windows Server 分布式文件系统 (DFS) 复制（也称为 DFS-R 或 DFSR）的问题。

有关 DFS 命名空间的信息，请参阅 [DFS 命名空间：常见问题解答](https://technet.microsoft.com/library/ee404780)。

有关 DFS 复制的新增功能信息，请参阅以下主题：

  - [DFS 命名空间和 DFS 复制概述](https://technet.microsoft.com/library/jj127250) (Windows Server 2012)  
      
  - [从 Windows Server 2008 到 Windows Server 2008 R2 的功能更改](https://technet.microsoft.com/library/dd391932)中的[分布式文件系统的新增功能](https://technet.microsoft.com/library/ee307957)主题  
      
  - [从 Windows Server 2003 SP1 到 Windows Server 2008 的功能更改](https://technet.microsoft.com/library/cc753208)中的[分布式文件系统](https://technet.microsoft.com/library/cc753479)主题  
      

有关本主题最近更改的列表，请参阅本主题的 [更改历史记录](#change-history) 部分。

      

## <a name="interoperability"></a>互操作性

### <a name="can-dfs-replication-communicate-with-frs"></a>DFS 复制是否可以与 FRS 通信？

不能。 DFS 复制不能与文件复制服务 (FRS) 通信。 DFS 复制和 FRS 可以在同一台服务器上同时运行，但绝不能将它们配置为复制相同的文件夹或子文件夹，因为这样做可能会导致数据丢失。

### <a name="can-dfs-replication-replace-frs-for-sysvol-replication"></a>DFS 复制是否可以代替 FRS 进行 SYSVOL 复制？

是的，在运行 Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 或 Windows Server 2008 的服务器上，DFS 复制可以代替 FRS 进行 SYSVOL 复制。 运行 Windows Server 2003 R2 的服务器不支持使用 DFS 复制来复制 SYSVOL 文件夹。

有关使用 DFS 复制来复制 SYSVOL 的详细信息，请参阅 [SYSVOL 复制迁移指南：从 FRS 迁移到 DFS 复制](https://technet.microsoft.com/library/dd640019)。

### <a name="can-i-upgrade-from-frs-to-dfs-replication-without-losing-configuration-settings"></a>是否可以在不丢失配置设置的情况下从 FRS 升级到 DFS 复制？

是的。 若要将复制从 FRS 迁移到 DFS 复制，请参阅以下文档：

  - 若要迁移除 SYSVOL 文件夹之外的文件夹复制，请参阅 [DFS 操作指南：从 FRS 迁移到 DFS 复制](https://go.microsoft.com/fwlink/?linkid=192776)和 [FRS2DFSR - FRS 到 DFSR 迁移实用工具](https://go.microsoft.com/fwlink/?linkid=195437) (https://go.microsoft.com/fwlink/?LinkID=195437) 。  
      
  - 若要将 SYSVOL 文件夹的复制迁移到 DFS 复制，请参阅 [SYSVOL 复制迁移指南：从 FRS 迁移到 DFS 复制](https://technet.microsoft.com/library/dd640019)。  
      

### <a name="can-i-use-dfs-replication-in-a-mixed-windowsunix-environment"></a>是否可以在混合的 Windows/UNIX 环境中使用 DFS 复制？

是的。 尽管 DFS 复制仅支持在运行 Windows Server 的服务器之间复制内容，但 UNIX 客户端可以访问 Windows 服务器上的文件共享。 为此，请在 DFS 复制服务器上安装网络文件系统 (NFS) 服务。

你还可以使用许多 UNIX 客户端中包含的 SMB/CIFS 客户端功能直接访问 Windows 文件共享，尽管此功能通常受到限制或需要修改 Windows 环境（例如使用组策略禁用 SMB 签名）。

DFS 复制与运行 Windows Server 操作系统的服务器上的 NFS 互操作，但不能复制 NFS 装入点。

### <a name="can-i-use-the-volume-shadow-copy-service-with-dfs-replication"></a>是否可以将卷影复制服务与 DFS 复制结合使用？

是的。 卷影复制服务 (VSS) 卷支持 DFS 复制，并且可以使用以前的版本客户端成功还原以前的快照。

### <a name="can-i-use-windowsbackup-ntbackupexe-to-remotely-back-up-a-replicated-folder"></a>是否可以使用 Windows 备份 (Ntbackup.exe) 远程备份复制文件夹？

不可以，不支持在运行 Windows Server 2003 或更低版本的计算机上使用 Windows 备份 (Ntbackup.exe) 对运行 Windows Server 2012、Windows Server 2008 R2 或 Windows Server 2008 的计算机上的复制文件夹中的内容进行复制。

若要备份存储在复制文件夹中的文件，请使用 Windows Server 备份或 Microsoft&reg; System Center Data Protection Manager。 有关 Windows Server 2008 R2 和 Windows Server 2008 中的备份和恢复功能的信息，请参阅[备份和恢复](https://technet.microsoft.com/library/Cc754097)。 有关详细信息，请参阅 [System Center Data Protection Manager](https://go.microsoft.com/fwlink/?linkid=182261) (https://go.microsoft.com/fwlink/?LinkId=182261) 。

### <a name="do-file-system-policies-impact-dfs-replication"></a>文件系统策略是否会影响 DFS 复制？

是的。 请勿在复制文件夹上配置文件系统策略。 文件系统策略在每个组策略刷新间隔重新应用 NTFS 权限。 这可能会导致共享冲突，因为在关闭文件之前，不会复制打开的文件。

### <a name="does-dfs-replication-replicate-mailboxes-hosted-on-microsoft-exchange-server"></a>DFS 复制是否可以复制 Microsoft Exchange Server 上托管的邮箱？

不能。 DFS 复制不能用于复制 Microsoft Exchange Server 上托管的邮箱。

### <a name="does-dfs-replication-support-file-screens-created-by-file-server-resource-manager"></a>DFS 复制是否支持由文件服务器资源管理器创建的文件屏蔽？

是的。 但是，文件服务器资源管理器 (FSRM) 文件屏蔽设置必须在复制的两端保持一致。 此外，DFS 复制具有自己的文件和文件夹筛选器机制，可用于从复制中排除某些文件和文件类型。

下面是实现文件屏蔽或配额的最佳做法：

  - 隐藏的 DfsrPrivate 文件夹不得使用配额或文件屏蔽。  
      
  - 启用屏蔽功能之前，任何复制文件夹中不得存在屏蔽的文件。  
      
  - 启用配额之前，任何文件夹都不能超过配额。  
      
  - 请务必谨慎使用硬配额。 复制组的各个成员可能会在复制前保持在配额范围内，但在复制文件时超出配额。 例如，如果用户将 10 兆字节 (MB) 文件复制到服务器 A（然后达到硬限制），而另一个用户将 5 MB 文件复制到服务器 B，则在下一次复制发生时，这两台服务器的配额都将超过 5 MB。 这可能会导致 DFS 复制不断地重试复制文件，从而造成版本向量出现漏洞，并可能导致性能问题。  
      

### <a name="is-dfs-replication-cluster-aware"></a>DFS 复制群集是否可识别？

是的，Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2008 R2 中的 DFS 复制包括将故障转移群集添加为复制组成员的功能。 有关详细信息，请参阅[将故障转移群集添加到复制组](https://go.microsoft.com/fwlink/?linkid=155085) (https://go.microsoft.com/fwlink/?LinkId=155085) 。 低于 Windows Server 2008 R2 的各 Windows 版本上的 DFS 复制服务并非旨在与故障转移群集配合使用，并且该服务不会故障转移到另一个节点。


> [!NOTE]
> DFS 复制不支持复制群集共享卷上的文件。 
<br>


### <a name="is-dfs-replication-compatible-with-data-deduplication"></a>DFS 复制与重复数据删除是否兼容？

是的，DFS 复制可以复制使用 Windows Server 中的重复数据删除的卷上的文件夹。

### <a name="is-dfs-replication-compatible-with-ris-and-wds"></a>DFS 复制与 RIS 以及 WDS 是否兼容？

是的。 DFS 复制对启用了单实例存储 (SIS) 的卷进行复制。 远程安装服务 (RIS)、Windows 部署服务 (WDS) 和 Windows Storage Server 都使用 SIS。

### <a name="is-it-possible-to-use-dfs-replication-with-offline-files"></a>是否可以将 DFS 复制用于脱机文件？

在一次只有一个用户写入文件的情况下，可以安全地使用 DFS 复制和脱机文件。 这适用于在两个分支机构之间浏览并希望能够在任一分支或脱机时访问其文件的用户。 脱机文件在本地缓存文件以供脱机使用，而 DFS 复制在每个分支机构之间复制数据。

请勿在多用户环境中将 DFS 复制用于脱机文件，因为 DFS 复制不提供任何分布式锁定机制或文件签出功能。 如果两个用户同时在不同的服务器上修改同一个文件，DFS 复制在下一次复制过程中会将旧文件移动到 DfsrPrivate\\ConflictandDeleted 文件夹（位于复制文件夹的本地路径下）。

### <a name="what-antivirus-applications-are-compatible-with-dfs-replication"></a>哪些防病毒应用程序与 DFS 复制兼容？

如果防病毒应用程序的扫描活动更改了复制文件夹中的文件，则可能会导致复制过多。 有关详细信息，请参阅[使用 DFS 复制测试防病毒应用程序的互操作性](https://go.microsoft.com/fwlink/?linkid=73990) (https://go.microsoft.com/fwlink/?LinkId=73990) 。

### <a name="what-are-the-benefits-of-using-dfs-replication-instead-of-windows-sharepoint-services"></a>使用 DFS 复制而不使用 Windows SharePoint Services 的好处有哪些？

Windows&reg; SharePoint&reg; Services 以文件签出功能的形式提供了密切的一致性，而 DFS 复制不具有此功能。 如果你担心多个人编辑同一个文件，建议使用 Windows SharePoint Services。 Windows Server 2003 R2 中提供了 Windows SharePoint Services 2.0 Service Pack 2。 Windows SharePoint Services 可以从 Microsoft 网站下载；Windows Server 的较新版本中不包含此功能。 但如果要跨多个站点复制数据，并且用户不会同时编辑相同的文件，建议使用 DFS 复制，以获取更大的带宽并简化管理。

## <a name="limitations-and-requirements"></a>限制和要求

### <a name="can-dfs-replication-replicate-between-branch-offices-without-a-vpn-connection"></a>DFS 复制是否可以在没有 VPN 连接的分支机构之间进行复制？

是 - 假设有一个连接到分支机构的专用广域网 (WAN) 链接（而不是 Internet）。 但必须在外部防火墙中打开正确的端口。 DFS 复制使用 RPC 终结点映射程序（端口 135）和一个随机分配的临时端口（1024 以上的端口）。 可使用 Dfsrdiag 命令行工具指定静态端口来代替临时端口  。 有关如何指定 RPC 端点映射程序的详细信息，请参阅 Microsoft 知识库 (https://go.microsoft.com/fwlink/?LinkId=73991) 中的[文章 154596](https://go.microsoft.com/fwlink/?linkid=73991)。

### <a name="can-dfs-replication-replicate-files-encrypted-with-the-encrypting-file-system"></a>DFS 复制是否可以使用加密文件系统复制加密的文件？

不能。 DFS 复制将不会复制使用加密文件系统 (EFS) 加密的文件或文件夹。 如果用户加密了先前复制的文件，则DFS 复制将从复制组的所有其他成员中删除该文件。 这可确保文件的唯一可用副本是服务器上的加密版本。

### <a name="can-dfs-replication-replicate-outlook-pst-or-microsoft-office-access-database-files"></a>DFS 复制是否可以复制 Outlook .pst 或 Microsoft Office Access 数据库文件？

只有在出于存档目的而存储了 Microsoft Outlook 个人文件夹文件 (.pst) 和 Microsoft Access 文件且无法使用 Outlook 或 Access 等客户端通过网络对其进行访问的情况下，DFS 复制才能安全地复制这些文件（若要打开 Outlook 或 Access 文件，请先将文件复制到本地存储设备）。 这样做的原因如下：

  - 通过网络连接打开 .pst 文件可能导致 .pst 文件中的数据损坏。 如需详细了解无法通过网络安全地访问 .pst 文件的原因，请参阅 Microsoft 知识库 (https://go.microsoft.com/fwlink/?LinkId=125363) 中的[文章 297019](https://go.microsoft.com/fwlink/?linkid=125363)。  
      
  - 通过 Outlook 或 Office Access 等客户端访问 .pst 和 Access 文件时，这些文件往往会长时间保持打开状态。 这样可以防止 DFS 复制在关闭这些文件之前复制这些文件。  
      

### <a name="can-i-use-dfs-replication-in-a-workgroup"></a>是否可以在工作组中使用 DFS 复制？

不能。 DFS 复制依赖于 Active Directory&reg; Domain Services 进行配置。 它仅在域中有效。

### <a name="can-more-than-one-folder-be-replicated-on-a-single-server"></a>是否可以在单个服务器上复制多个文件夹？

是的。 DFS 复制可以在多个服务器之间复制大量文件夹。 确保每个复制的文件夹都有唯一的根路径，并且这些路径不重叠。 例如，D:\\Sales 和 D:\\Accounting 可以是两个复制文件夹的根路径，但 D:\\Sales 和 D:\\Sales\\ 不能是两个复制文件夹的根路径。

### <a name="does-dfs-replication-require-dfs-namespaces"></a>DFS 复制是否需要 DFS 命名空间？

不能。 DFS 复制和 DFS 命名空间可以单独使用，也可以一起使用。 此外，DFS 复制可用于复制独立的 DFS 命名空间，而 FRS 无法做到这一点。

### <a name="does-dfs-replication-require-time-synchronization-between-servers"></a>DFS 复制在服务器之间是否要求时间同步？

不能。 DFS 复制没有明确要求在服务器之间实现时间同步。 但 DFS 复制确实要求各个服务器时钟接近相同。 必须在五分钟（默认值）内设置各个服务器时钟，Kerberos 身份验证才能正常运行。 例如，DFS 复制使用时间戳来确定发生冲突时哪个文件优先。 精确的时间对于垃圾回收、计划和其他功能也很重要。

### <a name="does-dfs-replication-support-replicating-an-entire-volume"></a>DFS 复制是否支持复制整个卷？

是的。 但是，必须先安装 Windows Server 2003 Service Pack 2 或修补程序。 有关详细信息，请参阅 Microsoft 知识库 (https://go.microsoft.com/fwlink/?LinkId=76776) 中的[文章 920335](https://go.microsoft.com/fwlink/?linkid=76776)。 此外，复制整个卷可能会导致以下问题：

  - 如果卷包含 Windows 页面文件，则复制将失败并会在系统事件日志中记录 DFSR 事件 4312。  
      
  - DFS 复制在目标服务器上的复制文件夹上设置系统属性和隐藏属性。 发生这种情况的原因是 Windows 默认情况下将系统属性和隐藏属性应用于卷根文件夹。 如果目标服务器上复制文件夹的本地路径也是卷根路径，则不会对文件夹属性进行进一步的更改。  
      
  - 在复制包含 Windows 系统文件夹的卷时，DFS 复制会识别 %WINDIR% 文件夹，并且不会对其进行复制。 但是，DFS 复制确实会复制非 Microsoft 应用程序使用的文件夹，如果应用程序与 DFS 复制存在互操作性问题，则可能导致应用程序在目标服务器上发生故障。  
      

### <a name="does-dfs-replication-support-rpc-over-http"></a>DFS 复制是否支持通过 HTTP 进行 RPC？

不能。

### <a name="does-dfs-replication-work-across-wireless-networks"></a>DFS 复制是否可以通过无线网络运行？

是的。 DFS 复制与连接类型无关。

### <a name="does-dfs-replication-work-on-refs-or-fat-volumes"></a>DFS 复制是在 ReFS 还是 FAT 卷上运行？

不能。 DFS 复制仅支持使用 NTFS 文件系统格式化的卷，不支持复原文件系统 (ReFS) 和 FAT 文件系统。 DFS 复制需要 NTFS，因为它使用 NTFS 文件系统的 NTFS 更改日志和其他功能。

### <a name="does-dfs-replication-work-with-sparse-files"></a>DFS 复制是否可以处理稀疏文件？

是的。 可以复制稀疏文件。 “稀疏”属性保留在接收成员上  。

### <a name="do-i-need-to-log-in-as-administrator-to-replicate-files"></a>是否必须以管理员身份登录才能复制文件？

不能。 DFS 复制是在本地系统帐户下运行的服务，因此你不需要以管理员身份登录即可进行复制。 但是，你必须是受影响的文件服务器的域管理员或本地管理员才能对 DFS 复制配置进行更改。

有关详细信息，请参阅[委派管理 DFS 复制的能力](https://go.microsoft.com/fwlink/?linkid=182294) (https://go.microsoft.com/fwlink/?LinkId=182294) 中的“DFS 复制安全性要求和委派”。

### <a name="how-can-i-upgrade-or-replace-a-dfs-replication-member"></a>如何升级或替换 DFS 复制成员？

若要升级或替换 DFS 复制成员，请参阅 Ask the Directory Services Team（咨询目录服务团队）博客上的博客文章：[替换 DFSR 成员硬件或 OS](https://blogs.technet.com/b/askds/archive/2010/09/10/series-wrap-up-and-downloads-replacing-dfsr-member-hardware-or-os.aspx)。

### <a name="is-dfs-replication-suitable-for-replicating-roaming-profiles"></a>DFS 复制是否适用于复制漫游策略文件？

是的。 复制漫游用户策略文件时，支持某些方案。 如需了解支持的方案，请参阅[Microsoft 关于复制用户配置文件数据的支持声明](https://go.microsoft.com/fwlink/?linkid=201282) (https://go.microsoft.com/fwlink/?LinkId=201282) 。

### <a name="is-there-a-file-character-limit-or-limit-to-the-folder-depth"></a>文件字符或文件夹深度是否存在限制？

Windows 和 DFS 复制支持的文件夹路径最多为 32000 个字符。 DFS 复制对 260 个字符的文件夹路径没有限制。

### <a name="must-members-of-a-replication-group-reside-in-the-same-domain"></a>复制组的成员是否必须位于同一个域中？

不能。 复制组可以跨越单个林中的多个域，但不能跨越不同的林。

### <a name="what-are-the-supported-limits-of-dfs-replication"></a>DFS 复制支持的限制是什么？

以下列表提供了一组经过 Microsoft 测试且适用于 Windows Server 2012 R2、Windows Server 2016 和 Windows Server 2019 的可伸缩性指南

  - 服务器上所有复制文件的大小：100 TB。  
      
  - 卷上的已复制文件数：7000 万。  
      
  - 最大文件大小：250 GB。  
      


> [!IMPORTANT]
> 创建包含大量文件的复制组时，我们建议导出数据库克隆，并使用预种子设定技术以最大程度地缩短初始复制的持续时间。 有关详细信息，请参阅 [Windows Server 2012 R2 中的 DFS 复制初始同步：克隆的攻击](https://techcommunity.microsoft.com/t5/Storage-at-Microsoft/DFS-Replication-Initial-Sync-in-Windows-Server-2012-R2-Attack-of/ba-p/424877)。 
<br>


以下列表提供了一组在 Windows Server 2012、Windows Server 2008 R2 和 Windows Server 2008 上经过 Microsoft 测试的可伸缩性指南：

  - 服务器上所有复制文件的大小：10 TB。  
      
  - 卷上的已复制文件数：1100 万。  
      
  - 最大文件大小：64 GB。  
      


> [!NOTE]
> 复制组、复制文件夹、连接或复制组成员的数量不再受到限制。 
<br>


有关 Microsoft 已针对 Windows Server 2003 R2 进行测试的可伸缩性指南的列表，请参阅 [DFS 复制可伸缩性指南](https://go.microsoft.com/fwlink/?linkid=75043) (https://go.microsoft.com/fwlink/?LinkId=75043) 。

### <a name="when-should-i-not-use-dfs-replication"></a>在什么情况下不应使用 DFS 复制？

请勿在多个用户同时在不同的服务器上更新或修改相同文件的环境中使用 DFS 复制。 这样做可能会导致 DFS 复制将文件的冲突副本移动到隐藏的 DfsrPrivate\\ConflictandDeleted 文件夹中。

如果多个用户需要同时在不同的服务器上修改相同的文件，请使用 Windows SharePoint Services 的文件签出功能，确保只有一个用户在处理文件。 Windows Server 2003 R2 中提供了 Windows SharePoint Services 2.0 Service Pack 2。 Windows SharePoint Services 可以从 Microsoft 网站下载；Windows Server 的较新版本中不包含此功能。

### <a name="why-is-a-schema-update-required-for-dfs-replication"></a>为什么 DFS 复制需要架构更新？

DFS 复制在 Active Directory 域服务的域命名上下文中使用新对象来存储配置信息。 这些对象是在更新 Active Directory 域服务架构时创建的。 有关详细信息，请参阅[查看 DFS 复制要求](https://go.microsoft.com/fwlink/?linkid=182264) (https://go.microsoft.com/fwlink/?LinkId=182264) 。

## <a name="monitoring-and-management-tools"></a>监视和管理工具

### <a name="can-i-automate-the-health-report-to-receive-warnings"></a>是否可以自动执行运行状况报告以接收警告？

是的。 可以通过三种方式自动执行运行状况报告：

  - 将 Windows Server 2012 R2 或 DfsrAdmin.exe 中包含的 DFSR Windows PowerShell 模块与计划任务结合使用，以便定期生成运行状况报告。 有关详细信息，请参阅[自动执行 DFS 复制运行状况报告](https://go.microsoft.com/fwlink/?linkid=74010) (https://go.microsoft.com/fwlink/?LinkId=74010) 。  
      
  - 使用适用于 System Center Operations Manager 的 DFS 复制管理包创建基于指定条件的警报。  
      
  - 使用 DFS 复制 WMI 提供程序为警报编写脚本。  
      

### <a name="can-i-use-microsoft-system-center-operations-manager-to-monitor-dfs-replication"></a>是否可以使用 Microsoft System Center Operations Manager 监视 DFS 复制？

是的。 有关详细信息，请参阅 Microsoft 下载中心 (https://go.microsoft.com/fwlink/?LinkId=182265) 中的[适用于 System Center Operations Manager 2007 的 DFS 复制管理包](https://go.microsoft.com/fwlink/?linkid=182265)。

### <a name="does-dfs-replication-support-remote-management"></a>DFS 复制是否支持远程管理？

是的。 DFS 复制使用 DFS 管理控制台和“添加复制组”命令支持远程管理  。 例如，在服务器 A 上，你可以连接到在以成员服务器 A 和 B 作为成员的林中定义的复制组。

Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008 和 Windows Server 2003 R2 都随附有 DFS 管理。 若要管理其他版本的 Windows DFS 复制，请使用远程桌面或[适用于 Windows 7 的远程服务器管理工具](https://technet.microsoft.com/library/Ee449475)。


> [!IMPORTANT]
> 若要查看或管理包含只读复制文件夹或故障转移群集成员的复制组，必须使用 Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 随附的 DFS 管理版本、<a href="https://go.microsoft.com/fwlink/p/?linkid=238560">适用于 Windows 8 的远程服务器管理工具</a>或<a href="https://technet.microsoft.com/library/ee449475">适用于 Windows 7 的远程服务器管理工具</a>。 
<br>


### <a name="do-ultrasound-and-sonar-work-with-dfs-replication"></a>超声波和声音波形是否适用 DFS 复制？

不能。 DFS 复制自带一组监视和诊断工具。 超声波和声音波形只能监视 FRS。

### <a name="how-can-files-be-recovered-from-the-conflictanddeleted-or-preexisting-folders"></a>如何从 ConflictAndDeleted 或 PreExisting 文件夹恢复文件？

若要恢复丢失的文件，请使用文件历史记录、文件资源管理器中的“还原先前版本”命令还原文件系统文件夹或共享文件夹中的文件，也可以从备份还原文件  。 若要从 ConflictAndDeleted 或 PreExisting 文件夹中直接恢复文件，请使用 `Get-DfsrPreservedFiles` 和 `Restore-DfsrPreservedFiles` Windows PowerShell cmdlet（包含在 Windows Server 2012 R2 中的 DFSR 模块中），或者 MSDN 代码库中的 [RestoreDFSR](https://code.msdn.microsoft.com/restoredfsr) 示例脚本。 此脚本仅用于灾难恢复且按原样提供，不提供任何担保。

### <a name="is-there-a-way-to-know-the-state-of-replication"></a>是否有什么方法可以了解复制状态？

是的。 复制监视有多种方法：

  - DFS 复制具有适用于 System Center Operations Manager 的管理包，可提供主动监视。  
      
  - DFS 管理为复制积压工作 (backlog)、复制效率以及给定复制组中的文件和文件夹数量提供内置的诊断报告。  
      
  - Windows Server 2012 R2 中的 DFSR Windows PowerShell 模块包含用于启动传播测试和编写传播和运行状况报告的 cmdlet。 有关详细信息，请参阅 [Windows PowerShell 中的分布式文件系统复制 Cmdlet](https://technet.microsoft.com/library/dn296601.aspx)。  
      
  - Dfsrdiag.exe 是一种命令行工具，可生成积压工作 (backlog) 计数或触发传播测试。 两者都可显示复制状态。 传播用于显示文件是否正被复制到所有节点。 积压工作 (backlog) 用于显示在两台计算机实现同步之前有多少文件仍需复制。积压工作 (backlog) 计数是指复制组成员尚未处理的更新数量。 在运行 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 的计算机上，Dfsrdiag.exe 还可显示 DFS 复制当前正在复制的更新。  
      
  - 脚本可使用 WMI 手动或通过 MOM 收集积压工作 (backlog) 信息。  
      

## <a name="performance"></a>性能

### <a name="does-dfs-replication-support-dial-up-connections"></a>DFS 复制是否支持拨号连接？

尽管 DFS 复制在拨号速度下可以运行，但如果要复制大量更改，它可能会出现工作积压的情况。 如果对现有文件进行少量更改，带有远程差分压缩 (RDC) 的 DFS 复制提供的性能将远超过直接复制文件。

### <a name="does-dfs-replication-perform-bandwidth-sensing"></a>DFS 复制是否执行带宽检测？

不能。 DFS 复制不执行带宽检测。 你可以配置 DFS 复制，使每个连接使用有限量的带宽（带宽限制）。 但在网络接口达到饱和时，DFS 复制不会进一步减少带宽占用，并且 DFS 复制会使链接在短时间内达到饱和。 通过 DFS 复制进行带宽限制并不完全准确，因为 DFS 复制通过限制 RPC 调用来限制带宽。 因此，较低级别的网络堆栈（包括 RPC）中的各种缓冲区可能会发生干扰，从而导致网络流量激增。

### <a name="does-dfs-replication-throttle-bandwidth-per-schedule-per-server-or-per-connection"></a>DFS 复制是否按计划、按服务器或按连接限制带宽？

如果在指定计划时配置带宽限制，则该复制组的所有连接都将使用该设置进行带宽限制。 也可以使用 DFS 管理将带宽限制设置为连接级设置。

### <a name="does-dfs-replication-use-active-directory-domain-services-to-calculate-site-links-and-connection-costs"></a>DFS 复制是否使用 Active Directory 域服务来计算站点链接和连接成本？

不能。 DFS 复制使用管理员定义的拓扑，该拓扑与 Active Directory 域服务站点成本无关。

### <a name="how-can-i-improve-replication-performance"></a>如何提高复制性能？

若要了解优化复制性能的不同方法，请参阅[目录服务团队博客](https://blogs.technet.com/b/askds/)中的[优化 DFSR 的复制性能](https://blogs.technet.com/b/askds/archive/2010/03/31/tuning-replication-performance-in-dfsr-especially-on-win2008-r2.aspx)。

### <a name="how-does-dfs-replication-avoid-saturating-a-connection"></a>DFS 复制如何避免使某个连接达到饱和？

在 DFS 复制中，可以设置要在某个连接上使用的最大带宽，服务会保持相应级别的网络使用率。 这与后台智能传输服务 (BITS) 不同，如果设置正确，DFS 复制不会使连接达到饱和。

不过，带宽限制并非 100% 准确，并且 DFS 复制可能会使链接在短时间内达到饱和。 这是因为 DFS 复制通过限制 RPC 调用来限制带宽。 由于此过程依赖于较低级别的网络堆栈（包括 RPC）中的各种缓冲区，因此复制流量可能会突然增加，有时会使网络链接达到饱和。

Windows Server 2008 中的 DFS 复制包含了多个性能增强功能，如[分布式文件系统](https://technet.microsoft.com/library/Cc753479)（[从 Windows Server 2003 SP1 到 Windows Server 2008 的功能更改](https://technet.microsoft.com/library/cc753208)中的一个主题）中所述。

### <a name="how-does-dfs-replication-performance-compare-with-frs"></a>DFS 复制性能与 FRS 相比如何？

DFS 复制的速度比 FRS 快得多，尤其是在对大型文件进行少量更改，且已启用 RDC 的情况下。 例如，启用 RDC 时，对 2 MB 的 PowerPoint&reg; 演示文稿进行少量更改只会通过网络发送 60 KB，传输的字节数节省了 97%。

RDC 不适用于小于 64 KB 的文件，并且对不争用网络带宽的高速 LAN 可能没多大益处。 可以使用 DFS 管理基于每个连接禁用 RDC。

### <a name="how-frequently-does-dfs-replication-replicate-data"></a>DFS 复制复制数据的频率如何？

将根据你设置的计划复制数据。 例如，你可以将计划设置为 15 分钟的间隔，一周七天。 在这些间隔期间启用复制。 检测到文件更改后不久（通常在几秒钟内）复制启动。

复制组计划可以设置为通用协调世界时 (UTC)，而连接计划可以设置为接收成员的当地时间。 复制组跨多个时区时，应考虑到这一点。 当地时间是指成员承载入站连接的时间。 将计划设置为当地时间时，显示的入站连接和相应的出站连接的计划将反映时区差异。

### <a name="how-much-of-my-servers-system-resources-will-dfs-replication-consume"></a>DFS 复制将消耗多少服务器系统资源？

DFS 复制使用的磁盘、内存和 CPU 资源取决于许多因素，包括文件的数量和大小、更改的速率、复制组成员的数量以及复制文件夹的数量。 此外，某些资源更难以估算。 例如，用于 DFS 复制数据库的可扩展存储引擎 (ESE) 技术可能会消耗大量可用内存，它会按需求进行释放。 除 DFS 复制以外的应用程序可以承载于同一台服务器上，具体取决于服务器配置。 但在一个服务器上承载多个应用程序或服务器角色时，请务必先测试此配置，然后在生产环境中加以实现。

### <a name="what-happens-if-a-wan-link-fails-during-replication"></a>如果 WAN 链接在复制过程中失败，会发生什么情况？

如果连接中断，DFS 复制将计划打开时继续尝试复制。 DFS 复制事件日志中还会记录连接错误，可使用 MOM（主动通过警报）和 DFS 复制运行状况报告（在管理员运行它时被动进行）搜集这些错误。

## <a name="remote-differential-compression-details"></a>远程差分压缩详细信息

### <a name="are-changes-compressed-before-being-replicated"></a>在复制更改之前是否会对更改进行压缩？

是的。 对于所有文件类型，文件的更改部分在发送之前都需进行压缩，但以下文件类型除外，这些类型的文件已压缩：.wma、.wmv、.zip、.jpg、.mpg、.mpeg、.m1v、.mp2、.mp3、.mpa、.cab、.wav、.snd、.au、.asf、.wm、.avi、.z、.gz、.tgz 和 .frx。 在 Windows Server 2003 R2 中，无法配置这些文件类型的压缩设置。

### <a name="can-an-administrator-turn-off-rdc-or-change-the-threshold"></a>管理员是否可以关闭 RDC 或更改阈值？

是的。 可以通过给定连接的属性页关闭 RDC。 在没有带宽限制的快速局域网 (LAN) 链接上，或对于主要由小于 64 KB 的文件组成的复制组，禁用 RDC 可以减少 CPU 利用率和复制延迟。 如果选择在连接上禁用 RDC，请在更改前后测试复制效率，以验证复制性能是否得到改善。

使用 Dfsradmin Connection Set 命令、DFS 复制 WMI 提供程序或手动编辑配置 XML 文件，可以更改 RDC 大小阈值  。

### <a name="does-rdc-work-on-all-file-types"></a>RDC 是否适用于所有文件类型？

是的。 不管文件数据类型如何，RDC 都在块级别计算差异。 但在某些文件类型（如 Word 文档、PST 文件和 VHD 映像）上，RDC 的工作效率更高。

### <a name="how-does-rdc-work-on-a-compressed-file"></a>RDC 如何处理压缩文件？

DFS 复制使用 RDC 来计算文件中已更改的块，并且通过网络仅发送这些块。 DFS 复制不需要知道有关文件内容的任何信息，只需知道哪些块已更改。

### <a name="is-cross-file-rdc-enabled-when-upgrading-to-windows-server-enterprise-edition-or-datacenter-edition"></a>升级到 Windows Server Enterprise Edition 或 Datacenter Edition 时是否启用了跨文件 RDC？

Windows Server Standard Edition 不支持跨文件 RDC。 但是，如果升级到支持跨文件 RDC 的版本或复制连接的成员正在运行受支持的版本，则会自动启用该功能。 有关支持跨文件 RDC 的版本的列表，请参阅“Windows 操作系统的哪些版本支持跨文件 RDC？”

### <a name="is-rdc-true-block-level-replication"></a>RDC 是否为块级复制？

不能。 RDC 是一种用于压缩文件传输的通用协议。 DFS 复制在文件级别而不是磁盘块级别的块上使用 RDC。 RDC 将一个文件分成多个块。 对于文件中的每个块，它都会计算一个签名，该签名是可表示较大块的少量字节。 签名集将从服务器传输到客户端。 客户端将服务器签名与客户端签名进行比较。 然后，客户端请求服务器仅发送客户端上尚不存在的签名数据。

### <a name="what-happens-if-i-rename-a-file"></a>重命名文件会出现什么情况？

在下一次复制过程中，DFS 复制会重命名复制组的所有其他成员上的文件。 并使用唯一 ID 跟踪这些文件，因此重命名文件并将其移动到副本中都不会影响 DFS 复制复制文件的能力。

### <a name="what-is-cross-file-rdc"></a>什么是跨文件 RDC？

跨文件 RDC 允许 DFS 复制使用 RDC，即使客户端不存在具有相同名称的文件也是如此。 跨文件 RDC 使用启发法来确定与需要复制的文件类似的文件，并使用与复制文件相同的类似文件块，以便最大程度地减少通过 WAN 传输的数据量。 在此过程中，跨文件 RDC 最多可以使用五个相似文件的块。

若要使用跨文件 RDC，复制连接的一个成员必须运行支持跨文件 RDC 的 Windows 版本。 有关支持跨文件 RDC 的版本的列表，请参阅“Windows 操作系统的哪些版本支持跨文件 RDC？”

### <a name="what-is-rdc"></a>什么是 RDC？

远程差分压缩 (RDC) 是一种客户端-服务器协议，可用于通过带宽有限的网络有效地更新文件。 RDC 检测文件中数据的插入、删除和重新排列，从而使 DFS 复制仅在文件更新时复制更改。 默认情况下，RDC 仅用于大小为 64 KB 及以上的文件。 RDC 可以在复制文件夹或 DfsrPrivate\\ConflictandDeleted 文件夹（位于复制文件夹的本地路径下）中使用同名文件的旧版本。

### <a name="when-is-rdc-used-for-replication"></a>RDC 何时用于复制？

文件超过最小大小阈值时，使用 RDC。 默认情况下，此大小阈值为 64 KB。 复制超过该阈值的文件后，除非该文件的大部分内容都发生了更改或 RDC 处于禁用状态，否则该文件的更新版本将始终使用 RDC。

### <a name="which-editions-of-the-windows-operating-system-support-cross-file-rdc"></a>Windows 操作系统的哪些版本支持跨文件 RDC？

要使用跨文件 RDC，复制连接的一个成员必须运行支持跨文件 RDC 的 Windows 操作系统版本。 下表显示了支持跨文件 RDC 的 Windows 操作系统版本。

### <a name="cross-file-rdc-availability-in-editions-of-the-windows-operating-system"></a>Windows 操作系统版本中的跨文件 RDC 可用性

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>操作系统版本</th>
<th>Standard Edition</th>
<th>企业版</th>
<th>Datacenter Edition</th>
</tr>
</thead>
<tbody>
<tr class="even">
<td><p>Windows Server 2012 R2</p></td>
<td><p>是<em></p></td>
<td><p>不可用</p></td>
<td><p>是</em></p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2012</p></td>
<td><p>是</p></td>
<td><p>不可用</p></td>
<td><p>是</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2008 R2</p></td>
<td><p>否</p></td>
<td><p>是</p></td>
<td><p>是</p></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2008</p></td>
<td><p>否</p></td>
<td><p>是</p></td>
<td><p>否</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2003 R2</p></td>
<td><p>否</p></td>
<td><p>是</p></td>
<td><p>否</p></td>
</tr>
</tbody>
</table>

\* 你可以选择在 Windows Server 2012 R2 上禁用跨文件 RDC。

## <a name="replication-details"></a>复制详细信息

### <a name="can-i-change-the-path-for-a-replicated-folder-after-it-is-created"></a>创建复制文件夹后，是否可以更改其路径？

不能。 如果需要更改复制文件夹的路径，必须在 DFS 管理中将删除该路径，并将其作为新的复制文件夹重新添加。 然后，DFS 复制会使用远程差分压缩 (RDC) 来执行同步，以确定发送成员和接收成员上的数据是否相同。 它不会再次复制文件夹中的所有数据。

### <a name="can-i-configure-which-file-attributes-are-replicated"></a>是否可以配置要复制的文件属性？

不可以，不可配置 DFS 复制复制的文件属性。

有关属性值及其说明的列表，请参阅 MSDN (https://go.microsoft.com/fwlink/?LinkId=182268) 上的[文件属性](https://go.microsoft.com/fwlink/?linkid=182268)。

通过使用 `SetFileAttributes dwFileAttributes` 函数设置以下属性值，并通过 DFS 复制对其进行复制。 对这些属性值进行更改会触发属性复制。 除非内容也发生更改，否则不会复制文件的内容。 有关详细信息，请参阅 MSDN 库 (https://go.microsoft.com/fwlink/?LinkId=182269) 中的 [SetFileAttributes 函数](https://go.microsoft.com/fwlink/?linkid=182269)。

  - FILE\_ATTRIBUTE\_HIDDEN  
      
  - FILE\_ATTRIBUTE\_READONLY  
      
  - FILE\_ATTRIBUTE\_SYSTEM  
      
  - FILE\_ATTRIBUTE\_NOT\_CONTENT\_INDEXED  
      
  - FILE\_ATTRIBUTE\_OFFLINE  
      

以下属性值通过 DFS 复制进行复制，但它们不会触发复制。

  - FILE\_ATTRIBUTE\_ARCHIVE  
      
  - FILE\_ATTRIBUTE\_NORMAL  
      

以下文件属性值也可以触发复制，尽管无法使用 `SetFileAttributes` 函数对其进行设置（使用 `GetFileAttributes` 函数查看属性值）。

  - FILE\_ATTRIBUTE\_REPARSE\_POINT  
      

> [!NOTE]
> 除非重新分析标记为 IO_REPARSE_TAG_SYMLINK，否则 DFS 复制不会复制重新分析点属性值。 带有 IO_REPARSE_TAG_DEDUP、IO_REPARSE_TAG_SIS 或 IO_REPARSE_TAG_HSM 重新分析标记的文件作为普通文件复制。 但是，重新分析标记和重新分析数据缓冲区不会复制到其他服务器，因为重新分析点仅适用于本地系统。 
<br>

  - FILE\_ATTRIBUTE\_COMPRESSED  
      
  - FILE\_ATTRIBUTE\_ENCRYPTED  
      

> [!NOTE]
> DFS 复制不会复制使用加密文件系统 (EFS) 加密的文件。 DFS 复制可以复制使用非 Microsoft 软件加密的文件，但前提是没有在文件上设置 FILE_ATTRIBUTE_ENCRYPTED 属性值。 
<br>

  - FILE\_ATTRIBUTE\_SPARSE\_FILE  
      
  - FILE\_ATTRIBUTE\_DIRECTORY  
      

DFS 复制不会复制 FILE\_ATTRIBUTE\_TEMPORARY 值。

### <a name="can-i-control-which-member-is-replicated"></a>是否可以控制要复制的成员？

是的。 创建复制组时，可以选择拓扑。 也可以选择“无拓扑”并在创建复制组之后手动配置连接  。

### <a name="can-i-seed-a-replication-group-member-with-data-prior-to-the-initial-replication"></a>在初始复制之前，是否可以使用数据作为复制组成员的种子？

是的。 DFS 复制支持在初始复制之前将文件复制到复制组成员。 这种“预留”可以显著减少在初始复制期间复制的数据量。

如果文件仅在实属性或时间戳方面有所差异，则初始复制不需要复制内容。 实属性是一种可以通过 Win32 函数 `SetFileAttributes` 设置的属性。 有关详细信息，请参阅 MSDN 库 (https://go.microsoft.com/fwlink/?LinkId=182269) 中的 [SetFileAttributes 函数](https://go.microsoft.com/fwlink/?linkid=182269)。 如果两个文件的其他属性（例如压缩）不同，则将复制文件的内容。

要预留复制组成员，请将文件复制到目标服务器上的相应文件夹中，创建复制组，然后选择主成员。 请选择包含要复制的最新文件的成员，因为主成员的内容被视为“具有权威性”。 这意味着在初始复制期间，主成员的文件将始终覆盖复制组的其他成员上其他版本的文件。

有关预设定种子和克隆 DFSR 数据库的信息，请参阅 [Windows Server 2012 R2 中的 DFS 复制初始同步：克隆的攻击](https://blogs.technet.com/b/filecab/archive/2013/08/21/dfs-replication-initial-sync-in-windows-server-2012-r2-attack-of-the-clones.aspx)。

有关初始复制的详细信息，请参阅[创建复制组](https://technet.microsoft.com/library/cc725893)。

### <a name="does-dfs-replication-overcome-common-file-replication-service-issues"></a>DFS 复制是否可以解决常见的文件复制服务问题？

是的。 DFS 复制可解决三个常见的 FRS 问题：

  - 日志覆盖：DFS 复制可从日记覆盖中动态恢复。 每个现有文件或文件夹都将被标记为 journalWrap 并针对文件系统进行验证，然后再重新启动复制。 在恢复期间，此卷在任一方向上都不可用于复制。  
      
  - 过量复制：为防止过量复制，DFS 复制使用额度系统。  
      
  - Morphed 文件夹：为了防止 Morphed 文件夹名称，DFS 复制将冲突数据存储在隐藏的 DfsrPrivate\\ConflictandDeleted 文件夹中（位于复制文件夹的本地路径下）。 例如，在使用 FRS 复制的不同服务器上同时创建具有相同名称的多个文件夹会导致 FRS 对旧文件夹进行重命名。 DFS 复制转而将旧文件夹移动到本地“Conflict and Deleted”文件夹。  
      

### <a name="does-dfs-replication-replicate-files-in-chronological-order"></a>DFS 复制是否按时间顺序复制文件？

不能。 文件可能不按顺序进行复制。

### <a name="does-dfs-replication-replicate-files-that-are-being-used-by-another-application"></a>DFS 复制是否可以复制其他应用程序正在使用的文件？

如果某个应用程序打开一个文件并在该文件上创建文件锁（用于防止打开该文件时其他应用程序使用该文件），则在关闭文件之前，DFS 复制不会复制该文件。 如果应用程序使用读取-共享访问权限打开文件，则仍可以复制文件。

### <a name="does-dfs-replication-replicate-ntfs-file-permissions-alternate-data-streams-hard-links-and-reparse-points"></a>DFS 复制是否会复制 NTFS 文件权限、备用数据流、硬链接和重新分析点？

  - DFS 复制会复制 NTFS 文件权限和备用数据流。  
      
  - Microsoft 不支持在复制文件夹中的文件之间创建 NTFS 硬链接，这样做会导致受影响文件出现复制问题。 硬链接文件将被 DFS 复制忽略，并且不会被复制。 交接点也不会被复制，并且 DFS 复制会为其遇到的每个交接点记录事件 4406。  
      
  - 通过 DFS 复制进行复制的唯一重新分析点是使用 IO\_REPARSE\_TAG\_SYMLINK 标记的重新分析点；但 DFS 复制不保证还会复制符号链接的目标。 有关详细信息，请参阅[目录服务团队博客](https://blogs.technet.com/b/askds/archive/2011/09/30/friday-mail-sack-super-slo-mo-edition.aspx)。  
      
  - 带有 IO\_REPARSE\_TAG\_DEDUP、IO\_REPARSE\_TAG\_SIS 或 IO\_REPARSE\_TAG\_HSM 重新分析标记的文件作为普通文件复制。 重新分析标记和重新分析数据缓冲区不会复制到其他服务器，因为重新分析点仅适用于本地系统。 因此，DFS 复制可以在使用 Windows Server 2012 中的重复数据删除的卷上或单实例存储 (SIS) 上复制文件夹，但是，每个启用了角色服务的服务器都将单独维护重复数据删除信息。  
      

### <a name="does-dfs-replication-replicate-timestamp-changes-if-no-other-changes-are-made-to-the-file"></a>如果未对该文件进行其他更改，DFS 复制是否可以复制时间戳更改？

不可以，DFS 复制不会复制仅更改时间戳的文件。 此外，更改后的时间戳不会复制到复制组的其他成员，除非对文件进行了其他更改。

### <a name="does-dfs-replication-replicate-updated-permissions-on-a-file-or-folder"></a>DFS 复制是否可以复制文件或文件夹上的更新权限？

是的。 DFS 复制会复制文件和文件夹的权限更改。 仅复制与访问控制列表 (ACL) 关联的文件的一部分，不过 DFS 复制仍必须将整个文件读入暂存区域。


> [!NOTE]
> 更改大量文件上的 ACL 可能会影响复制性能。 但是，使用 RDC 时，传输的数据量与 ACL 的大小成正比，而不与整个文件的大小成正比。 磁盘流量的大小仍与文件大小成正比，因为必须在暂存文件夹中读取文件或从暂存文件夹读取文件。 
<br>


### <a name="does-dfs-replication-support-merging-text-files-in-the-event-of-a-conflict"></a>发生冲突时，DFS 复制是否支持合并文本文件？

存在冲突时，DFS 复制不会合并文件。 但是，它确实会尝试将文件的较旧版本保留在检测到冲突的计算机上的隐藏 DfsrPrivate\\ConflictandDeleted 文件夹中。

### <a name="does-dfs-replication-use-encryption-when-transmitting-data"></a>传输数据时，DFS 复制是否使用加密？

是的。 DFS 复制使用加密的远程过程调用 (RPC) 连接。

### <a name="is-it-possible-to-disable-the-use-of-encrypted-rpc"></a>是否可以禁用加密的 RPC？

不能。 DFS 复制服务使用远程过程调用 (RPC) 通过 TCP 复制数据。 为了保护通过 Internet 的数据传输，DFS 复制服务设计为始终使用身份验证级别的常量 `RPC_C_AUTHN_LEVEL_PKT_PRIVACY`。 这样可确保通过 Internet 进行的 RPC 通信始终是加密的。 因此，不能禁用 DFS 复制服务使用加密 RPC。

有关详细信息，请参阅以下 Microsoft 网站：

  - [RPC 技术参考](https://go.microsoft.com/fwlink/?linkid=182278)  
      
  - [关于远程差分压缩](https://go.microsoft.com/fwlink/?linkid=182279)  
      
  - [身份验证级别常量](https://go.microsoft.com/fwlink/?linkid=182280)  
      

### <a name="how-are-simultaneous-replications-handled"></a>如何处理同步复制？

每个复制文件夹都有一个更新管理器。 更新管理器彼此独立运行。

默认情况下，所有连接和复制组之间最多共享 16 个并发下载（Windows Server 2003 R2 中为 4 个）。 由于未序列化连接和复制组更新，因此接收更新没有特定的顺序。 如果打开了两个计划，则通常会同时从两个连接中接收并安装更新。

### <a name="how-do-i-force-replication-or-polling"></a>如何实现强制执行复制或轮询？

可以使用[编辑复制计划](https://technet.microsoft.com/library/Cc732278)中所介绍的 DFS 管理立即强制执行复制。 也可以使用 Windows Server 2012 R2 随附的 DFSR PowerShell 模块中包含的 `Sync-DfsReplicationGroup` cmdlet 或 Dfsrdiag SyncNow 命令强制执行复制  。 可以使用 `Update-DfsrConfigurationFromAD` cmdlet 或 Dfsrdiag.exe PollAD 命令强制执行轮询  。

### <a name="is-it-possible-to-configure-a-quiet-time-between-replications-for-files-that-change-frequently"></a>对于频繁更改的文件，是否可以配置复制之间的安静时间？

不能。 如果打开此计划，则 DFS 复制将在发现更改时复制这些更改。 无法为文件配置安静时间。

### <a name="is-it-possible-to-configure-one-way-replication-with-dfs-replication"></a>是否可以使用 DFS 复制配置单向复制？

是的。 如果使用的是 Windows Server 2012 或 Windows Server 2008 R2，则可以创建一个通过单向连接复制内容的只读复制文件夹。 有关详细信息，请参阅[使复制文件夹对特定成员只读](https://go.microsoft.com/fwlink/?linkid=156740) (https://go.microsoft.com/fwlink/?LinkId=156740) 。

我们不支持在 Windows Server 2008 或 Windows Server 2003 R2 中使用 DFS 复制创建单向复制连接。 这样做可能会导致许多问题，包括运行状况检查拓扑错误、暂存问题以及 DFS 复制数据库相关问题。

如果使用的是 Windows Server 2008 或 Windows Server 2003 R2，则可以通过执行以下操作来模拟单向连接：

  - 告知管理员仅对你想指定为主服务器的服务器进行更改。 然后让更改复制到目标服务器上。  
      
  - 在目标服务器上配置共享权限，使最终用户没有写入权限。 如果不允许对分支服务器进行更改，则不会往回复制任何内容，从而可以模拟单向连接并保持较低的 WAN 使用率。  
      

### <a name="is-there-a-way-to-force-a-complete-replication-of-all-files-including-unchanged-files"></a>是否有办法强制完全复制所有文件（包括未更改的文件）？

不能。 如果 DFS 复制认为文件相同，则不会复制这些文件。 如果尚未复制更改后的文件，DFS 复制将在配置后自动复制这些文件。 要覆盖配置的计划，请使用 WMI 方法 ForceReplicate()  。 但这只是一个计划覆盖，它不会强制复制未更改的文件或相同的文件。

### <a name="what-happens-if-the-primary-member-suffers-a-database-loss-during-initial-replication"></a>如果在初始复制期间主成员出现数据库丢失，会发生什么情况？

在初始复制期间，如果接收成员拥有与主成员上的文件的版本不同的文件，则在解决冲突时将始终优先处理主成员的文件。 主成员名称存储在 Active Directory 域服务中，该名称在主成员准备进行复制之后、复制组的所有成员进行复制之前将被清除。

如果初始复制失败或 DFS 复制服务在复制过程中重启，则主成员将在本地 DFS 复制数据库中看到主成员名称并重新尝试初始复制。 如果在清除 Active Directory 域服务中的主名称之后，但是在复制组的所有成员完成初始复制之前，主成员的 DFS 复制数据库丢失，则该复制组的所有成员都无法复制文件夹，因为没有将任何服务器指定为主成员。 如果发生这种情况，请在主成员服务器上使用 Dfsradmin membership /set /isprimary:true 命令手动还原主成员名称  。

有关初始复制的详细信息，请参阅[创建复制组](https://technet.microsoft.com/library/cc725893)。


> [!WARNING]
> 主成员名称仅在初始复制过程中使用。 如果在复制完成后使用 <STRONG>Dfsradmin</STRONG> 命令指定复制文件夹的主成员，DFS 复制不会将服务器指定为 Active Directory 域服务中的主成员。 但是，如果服务器上的 DFS 复制数据库随后遭受不可恢复的破坏或数据丢失，则服务器将尝试以初始成员身份执行初始复制，而不是以复制组的其他成员身份恢复其数据。 实质上，服务器会成为非授权主服务器，这可能会导致冲突。 因此，仅在确定初始复制便失败时，才手动指定主成员。 
<br>


### <a name="what-happens-if-the-replication-schedule-closes-while-a-file-is-being-replicated"></a>如果复制计划在文件复制过程中关闭，会发生什么情况？

如果在连接时启用了远程差分压缩 (RDC)，则大于 64 KB 的文件的入站复制将在计划关闭之前立即开始复制（或更改为“无带宽”  ），并在计划打开后继续复制（或更改为“无带宽”以外的内容  ）。 复制从复制停止时的状态继续。

如果 RDC 处于关闭状态，DFS 复制将完全重启文件传输。 文件在接收成员上可用时，这可能会延迟。

### <a name="what-happens-when-two-users-simultaneously-update-the-same-file-on-different-servers"></a>当两个用户同时在不同服务器上更新同一文件时会发生什么情况？

当 DFS 复制检测到冲突时，它将使用最新保存的文件版本。 它会将另一个文件移到 DfsrPrivate\\ConflictandDeleted 文件夹中（位于解决冲突的计算机上的复制文件夹的本地路径下）。 除非在“Conflict and Deleted”文件夹超过配置的大小或 DFS 复制遇到磁盘空间不足错误时清除了“Conflict and Deleted”文件夹，否则文件会一直保留在那里。 不会复制“Conflict and Deleted”文件夹，并且这种冲突解决方法避免了 FRS 中可能出现的仿形目录问题。

发生冲突时，DFS 复制将信息性事件记录到 DFS 复制事件日志中。 此事件不需要用户操作，原因如下：

  - 它对用户不可见（仅对服务器管理员可见）。  
      
  - DFS 复制将“Conflict and Deleted”文件夹视为缓存。 达到配额阈值时，它会清除其中某些文件。 不保证会保存发生冲突的文件。  
      
  - 冲突可能驻留在与冲突起源不同的服务器上。  
      

## <a name="staging"></a>分步

### <a name="does-dfs-replication-continue-staging-files-when-replication-is-disabled-by-a-schedule-or-bandwidth-throttling-quota-or-when-a-connection-is-manually-disabled"></a>按计划或带宽限制配额禁用复制或手动禁用连接时，DFS 复制是否继续暂存文件？

不能。 如果超出了带宽限制配额，或者禁用了连接，DFS 复制不会继续在计划复制时间之外暂存文件。

### <a name="does-dfs-replication-prevent-other-applications-from-accessing-a-file-during-staging"></a>DFS 复制是否会阻止其他应用程序在暂存期间访问文件？

不能。 DFS 复制以不阻止用户或应用程序打开复制文件夹中的文件的方式打开文件。 此方法称为“机会锁定”。

### <a name="is-it-possible-to-change-the-location-of-the-staging-folder-with-the-dfs-management-tool"></a>是否可以通过 DFS 管理工具更改暂存文件夹的位置？

是的。 在复制组的每个成员的“属性”对话框的“高级”选项卡上配置暂存文件夹的位置   。

### <a name="when-are-files-staged"></a>何时暂存文件？

如下表所示，当接收成员请求文件（除非文件大小不超过 64 KB）时，文件在发送成员上暂存。 如果在连接上禁用了远程差分压缩 (RDC)，则文件将暂存，除非文件大小不超过 256 KB。 如果文件大小小于 64 KB，则在传输文件时也会在接收成员上暂存文件，不过你可以将此设置配置为在 16 KB 到 1 MB 之间。 如果计划已关闭，则不会暂存文件。

### <a name="the-minimum-file-sizes-for-staging-files"></a>暂存文件的最小文件大小

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th> </th>
<th>已启用 RDC</th>
<th>已禁用 RDC</th>
</tr>
</thead>
<tbody>
<tr class="even">
<td><p>发送成员</p></td>
<td><p>64 KB</p></td>
<td><p>256 KB</p></td>
</tr>
<tr class="odd">
<td><p>接收成员</p></td>
<td><p>默认值为 64 KB</p></td>
<td><p>默认值为 64 KB</p></td>
</tr>
</tbody>
</table>

### <a name="what-happens-if-a-file-is-changed-after-it-is-staged-but-before-it-is-completely-transmitted-to-the-remote-site"></a>如果文件在暂存之后但在完全传输到远程站点之前发生了更改，会发生什么情况？

如果文件的任何部分正在传输，DFS 复制将继续传输。 如果在 DFS 复制开始传输文件之前更改了文件，则将发送该文件的较新版本。

## <a name="change-history"></a>更改历史记录


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>日期</th>
<th>说明</th>
<th>原因</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2018 年 11 月 15 日</p></td>
<td><p>已更新 Windows Server 2019。</p></td>
<td><p>新的操作系统。</p></td>
</tr>
<tr class="even">
<td><p>2013 年 10 月 9 日</p></td>
<td><p>“已更新 DFS 复制受支持的限制是什么？”部分包含来自 Windows Server 2012 R2 的测试结果。</p></td>
<td><p>Windows Server 最新版本的更新</p></td>
</tr>
<tr class="odd">
<td><p>2013 年 1 月 30 日</p></td>
<td><p>添加了“按计划或带宽限制配额禁用复制或手动禁用连接时，DFS 复制是否继续暂存文件？”条目。</p></td>
<td><p>客户问题</p></td>
</tr>
<tr class="even">
<td><p>2012 年 10 月 31 日</p></td>
<td><p>编辑了“DFS 复制受支持的限制是什么？”条目以增加卷上已测试的复制文件数。</p></td>
<td><p>客户反馈</p></td>
</tr>
<tr class="odd">
<td><p>2012 年 8 月 15 日</p></td>
<td><p>编辑了“DFS 复制是否可以复制 NTFS 文件权限、备用数据流、硬链接和重新分析点？”条目以进一步阐明 DFS 复制如何处理硬链接和重新分析点。</p></td>
<td><p>来自客户支持服务的反馈</p></td>
</tr>
<tr class="even">
<td><p>2012 年 6 月 13 日</p></td>
<td><p>编辑了“DFS 复制是否适用于 ReFS 或 FAT 卷？”条目以添加有关 ReFS 的讨论。</p></td>
<td><p>客户反馈</p></td>
</tr>
<tr class="odd">
<td><p>2012 年 4 月 25 日</p></td>
<td><p>编辑了“DFS 复制是否可以复制 NTFS 文件权限、备用数据流、硬链接和重新分析点？”条目以阐明 DFS 复制如何处理硬链接。</p></td>
<td><p>减少可能产生的困惑</p></td>
</tr>
<tr class="even">
<td><p>2011 年 3 月 30 日</p></td>
<td><p>编辑了“DFS 复制是否可以复制 Outlook .pst 或 Microsoft Office Access 数据库文件？”条目以更正将 DFS 复制用于 .pst 文件和 Access 文件可能产生的影响。</p>
<p>添加了“如何提高复制性能？”</p></td>
<td><p>客户对上一个条目的疑问，上一个条目错误地指出复制 .pst 文件或 Access 文件可能会损坏 DFS 复制数据库。</p></td>
</tr>
<tr class="odd">
<td><p>2011 年 1 月 26 日</p></td>
<td><p>添加了“如何从 ConflictAndDeleted 或 PreExisting 文件夹恢复文件？”</p></td>
<td><p>客户反馈</p></td>
</tr>
<tr class="even">
<td><p>2010 年 10 月 20 日</p></td>
<td><p>添加了“如何升级或替换 DFS 复制成员？”</p></td>
<td><p>客户反馈</p></td>
</tr>
</tbody>
</table>

