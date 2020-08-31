---
title: 安全地虚拟化 Active Directory 域服务 (AD DS)
description: Active Directory 的 USN 回滚和安全虚拟化
ms.topic: article
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 03/22/2019
ms.assetid: 7a3114c8-bda8-49bb-83a8-4e04340ab221
ms.openlocfilehash: fbacb87d99bf5b396e119028e15e8a4aa0c9ef53
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88940977"
---
# <a name="safely-virtualizing-active-directory-domain-services-ad-ds"></a>安全地虚拟化 Active Directory 域服务 (AD DS)

>适用于：Windows Server

从 Windows Server 2012 开始，通过引入虚拟化安全功能，AD DS 针对域控制器虚拟化提供了更多的支持。 本文介绍了域控制器复制中的 USN 和 InvocationID 的角色，并讨论了可能会出现的一些潜在问题。

## <a name="update-sequence-number-and-invocationid"></a>更新序列号和 InvocationID

虚拟环境对取决于基于逻辑时钟的复制方案的分布式工作负荷，提出了独特的挑战。 例如，AD DS 复制使用分配给每个域控制器上的事务的单调递增的值（称为 USN 或更新序列号）。 每个域控制器的数据库实例也有标识，称为 InvocationID。 域控制器的 InvocationID 和其 USN 一起作为一个唯一标识符，该标识符与在每个域控制器上执行的每个写入事务相关联，并且在林中必须是唯一的。

AD DS 复制使用每个域控制器上的 InvocationID 和 USN 来确定需要复制到其他域控制器的更改。 如果一个域控制器在域控制器感知之外及时回滚，并且 USN 重复用于完全不同的事务，则复制将无法聚合，因为其他域控制器会认为它们已经收到了与该 InvocationID 环境下的重复使用的 USN 相关联的更新。

例如，下图显示了当在 VDC2（在虚拟机上运行的目标域控制器）上检测到 USN 回滚时在 Windows Server 2008 R2 和更早版本的操作系统上所发生事件的顺序。 此图中，在复制伙伴检测到 VDC2 已发送最新 USN 值(以前由复制伙伴检测到，表示 VDC2 的数据库已及时不正确地回滚）时，VDC2 上将进行 USN 回滚的检测。

![检测到 USN 回滚时的事件序列](../media/Introduction-to-Active-Directory-Domain-Services--AD-DS--Virtualization--Level-100-/ADDS_Exampleofhowreplicationcanbecomeinconsistent.png)

例如，应用在域控制器感知之外的快照，虚拟机 (VM) 轻松地让虚拟机监控程序管理员回滚域控制器的 USN（其逻辑时钟）。 有关 USN 和 USN 回滚的详细信息，包括演示未检测到的 USN 回滚实例的另一个图，请参阅 [USN 和 USN 回滚](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd363553(v=ws.10)#usn_and_usn_rollback)。

从 Windows Server 2012 开始，如果虚拟机通过虚拟机快照应用程序及时回滚，则托管在虚拟机监控程序平台（显示称为虚拟机生成 ID 的标识符）的 AD DS 虚拟域控制器可以检测和采取必要的安全措施保护 AD DS 环境。 因为虚拟机生成 ID 设计使用虚拟机监控程序供应商独立机制在来宾虚拟机地址空间中显示此标识符，所以安全虚拟化体验对支持虚拟机生成 ID 的任何虚拟机监控程序来说始终可用。 如果虚拟机已及时回滚，则此标识符可以通过在虚拟机内运行的服务和应用程序进行采样加以检测。

## <a name="effects-of-usn-rollback"></a>USN 回滚的影响

当发生 USN 回滚时，以前看到了 USN 的目标域控制器不会对对象和属性的修改进行入站复制。

因为这些目标域控制器认为它们是最新的，因此不会在目录服务事件日志中或通过监视和诊断工具报告复制错误。

USN 回滚可能会影响任何分区中的任何对象或属性的复制。 最常见的副作用是在回滚域控制器上创建的用户帐户和计算机帐户在一个或多个复制合作伙伴上不存在。 或者，在回滚域控制器上发起的密码更新在复制合作伙伴上不存在。

USN 回滚可能会阻止任何 Active Directory 分区中的任何对象类型进行复制。 这些对象类型包括：

* Active Directory 复制拓扑和计划
* 林中域控制器的存在和这些域控制器的角色
* 林中域和应用程序分区的存在
* 安全组及其当前组成员身份的存在
* Active Directory 集成 DNS 区域中的 DNS 记录注册

USN 孔的大小可能代表对用户、计算机、信任、密码和安全组所做的数百、数千甚至数万次更改。 USN 孔是由以下两者之间的差异定义的：在执行还原的系统状态备份时存在的最高 USN 编号，在回滚的域控制器脱机之前在其上创建的原发更改数。

## <a name="detecting-a-usn-rollback"></a>检测 USN 回滚

由于 USN 回滚很难检测到，因此，当源域控制器向目标域控制器发送以前确认的 USN 编号，而在调用 ID 中没有相应的更改时，域控制器会记录事件 2095。

为了防止在错误还原的域控制器上创建对 Active Directory 的唯一原发更新，将暂停网络登录服务。 当网络登录服务暂停时，用户和计算机帐户无法更改不对此类更改进行出站复制的域控制器上的密码。 同样，在对 Active Directory 中的对象进行更新时，Active Directory 管理工具将偏向使用正常运行的域控制器。

在域控制器上，如果满足以下条件，则会记录类似于以下内容的事件消息：

* 源域控制器向目标域控制器发送以前确认的 USN 编号。
* 调用 ID 中没有相应的更改。

可能会在目录服务事件日志中捕获这些事件。 但是，在管理员看到它们之前，它们可能会被覆盖。

如果怀疑已发生 USN 回退，但未在事件日志中看到对应的事件，请检查注册表中是否存在“DSA 不可写”条目。 此条目可以确凿地证明 USN 回滚已发生。

```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters
Registry entry: Dsa Not Writable
Value: 0x4
```

> [!WARNING]
> 删除或手动更改“DSA 不可写”注册表项值会将回滚域控制器置于永久不受支持的状态。 因此，不支持此类更改。 具体而言，修改该值将删除 USN 回滚检测代码添加的隔离行为。 回滚域控制器上的 Active Directory 分区将与同一 Active Directory 林中的直接和可传递复制伙伴永久不一致。

有关此注册表项和解决方法步骤的详细信息，请参阅支持文章 [Active Directory 复制错误 8456 或 8457：“源 |目标服务器当前拒绝复制请求”](https://support.microsoft.com/help/2023007/active-directory-replication-error-8456-or-8457-the-source-destination)。

## <a name="virtualization-based-safeguards"></a>基于虚拟化的安全措施

在域控制器安装期间，AD DS 最初将虚拟机生成 ID 标识符存储为其数据库（通常称为目录信息树，或 DIT)中域控制器计算机对象上的 msDS -GenerationID 属性的一部分。 虚拟机内的 Windows 驱动程序独立地跟踪虚拟机生成 ID。

当管理员从以前的快照还原虚拟机时，来自虚拟机驱动程序的虚拟机生成 ID 的当前值要与 DIT 中的值进行比较。

如果这两个值不相同，则重置 invocationID 并放弃 RID 池，从而防止重复使用 USN。 如果这两个值相同，则正常提交事务。

每次域控制器重新启动时，AD DS 也将来自虚拟机的虚拟机生成 ID 的当前值与 DIT 中的值进行比较，如果这两个值不相同，则它将重置 invocationID，放弃 RID 池，并使用新值更新 DIT。 它也非权威地同步 SYSVOL 文件夹，以完成安全还原。 这使安全措施扩展到关闭的虚拟机上快照的应用程序。 Windows Server 2012 中引入的这些安全措施使 AD DS 管理员能够受益于在虚拟化环境中部署和管理域控制器的独特优势。

下图显示了当在虚拟化域控制器（在支持虚拟机生成 ID 的虚拟机监控程序上运行 Windows Server 2012 ）上检测到相同的 USN 回滚时，如何应用虚拟化安全措施。

![检测到相同的 USN 回滚时应用的安全措施](../media/Introduction-to-Active-Directory-Domain-Services--AD-DS--Virtualization--Level-100-/ADDS_VDC_Exampleofhowsafeguardswork.gif)

在这种情况下，当虚拟机监控程序检测到虚拟机生成 ID 值更改时，将触发虚拟化安全措施，包括重置虚拟化 DC 的 InvocationID（在前面的示例中从 A 到 B），更新保存在虚拟机上的虚拟机生成 ID 值以匹配虚拟机监控程序存储的新值 (G2)。 安全措施确保两个域控制器的复制聚合。

在 Windows Server 2012 中，AD DS 使用（托管在虚拟机生成 ID 感知的虚拟机监控程序上的）虚拟域控制器上的安全措施，并确保意外的快照应用程序和其他此类虚拟机监控程序启用的机制（可以‘回滚’虚拟机状态）不会中断 AD DS 环境（通过防止 USN 泡沫或延迟对象等复制问题）。

不建议将通过应用虚拟机快照还原域控制器作为备份域控制器为一种替代机制。 建议你继续使用 Windows Server Backup 或其他基于 VSS 书写器的备份解决方案。

> [!CAUTION]
> 如果生产环境中的域控制器意外地还原到快照，建议你向供应商咨询应用程序、托管在该虚拟机上的服务、以及快照还原后验证这些程序状态的指南。

有关详细信息，请参阅 [Virtualized domain controller safe restore architecture](../ad-ds/get-started/virtual-dc/Virtualized-Domain-Controller-Architecture.md#BKMK_SafeRestoreArch)。

## <a name="recovering-from-a-usn-rollback"></a>通过 USN 回滚进行恢复

可以采用两种方法通过 USN 回滚进行恢复：

* 从域中删除域控制器
* 还原良好备份的系统状态

### <a name="remove-the-domain-controller-from-the-domain"></a>从域中删除域控制器

1. 从域控制器中删除 Active Directory，以强制使其成为独立服务器。
2. 关闭已降级的服务器。
3. 在运行状况良好的域控制器上，清除降级的域控制器的元数据。
4. 如果错误还原的域控制器承载着操作主机角色，请将这些角色转移到正常的域控制器。
5. 重启已降级的服务器。
6. 如果需要，请在独立服务器上再次安装 Active Directory。
7. 如果域控制器以前是全局编录，请将域控制器配置为全局编录。
8. 如果域控制器以前承载着操作主机角色，请将操作主机角色转移回域控制器。

### <a name="restore-the-system-state-of-a-good-backup"></a>还原良好备份的系统状态

评估此域控制器是否存在有效的系统状态备份。 如果在错误还原回滚域控制器之前创建了有效的系统状态备份，并且备份包含域控制器上所做的最新更改，请从最新备份还原系统状态。

还可以使用快照作为备份来源。 还可以使用[当没有合适的系统状态数据备份可用时还原虚拟域控制器](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd363553%28v%3dws.10%29#restoring-a-virtual-domain-controller-when-an-appropriate-system-state-data-backup-is-not-available)部分中的步骤来设置数据库，为其自己提供一个新的调用 ID

## <a name="next-steps"></a>后续步骤

* 有关虚拟域控制器的详细疑难解答信息，请参阅 [Virtualized Domain Controller Troubleshooting](../ad-ds/manage/virtual-dc/Virtualized-Domain-Controller-Troubleshooting.md)。
* [有关 Windows 时间服务 (W32Time) 的详细信息](../../networking/windows-time-service/windows-time-service-top.md)
