---
ms.assetid: e4c31187-f15f-410b-bb79-8d63e2f2b421
title: 将域控制器升级到 Windows Server 2012 R2 和 Windows Server 2012
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.openlocfilehash: 4034ea96fbe1f758d6948b2bc52ba9786158b0ba
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88940557"
---
# <a name="upgrade-domain-controllers-to-windows-server-2012-r2-and-windows-server-2012"></a>将域控制器升级到 Windows Server 2012 R2 和 Windows Server 2012

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

本主题提供有关 Windows Server 2012 R2 和 Windows Server 2012 中的 Active Directory 域服务的背景信息，并说明了从 Windows Server 2008 或 Windows Server 2008 R2 升级域控制器的过程。

## <a name="domain-controller-upgrade-steps"></a><a name="BKMK_UpgradeWorkflow"></a>域控制器升级步骤
升级域的推荐方法是根据需要提升运行较新版本 Windows Server 的域控制器并降级较旧的域控制器。 该方法优于升级现有域控制器的操作系统。 此列表涵盖在提升运行较新版本的 Windows Server 的域控制器之前要遵循的一般步骤：

1. 验证目标服务器是否满足 [系统要求](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn303418(v=ws.11))。
2. 验证[应用程序兼容性](../../ad-ds/deploy/Upgrade-Domain-Controllers-to-Windows-Server-2012-R2-and-Windows-Server-2012.md#BKMK_AppCompat)。
3. 验证安全设置。 有关详细信息，请参阅 windows [server 2012 中与 AD DS 相关的弃用功能和行为更改](../../ad-ds/deploy/Upgrade-Domain-Controllers-to-Windows-Server-2012-R2-and-Windows-Server-2012.md#BKMK_DeprecatedFeatures) 和 [windows Server 2008 和 Windows server 2008 R2 中的安全默认设置](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee522994(v=ws.10)#BKMK_SecureDefault)。
4. 从计划运行安装的计算机上检查与目标服务器的连接性。
5. 检查所需操作主机角色的可用性：

   - 若要在现有域和林中安装运行 Windows Server 2012 的第一个 DC，运行安装的计算机需要连接到架构主机，才能运行 adprep/forestprep 和基础结构主机以便运行 adprep/domainprep。
   - 若要在已扩展林架构的域中安装第一个 DC，则只需连接至结构主机即可。
   - 若要在现有林中安装或删除域，则需要连接至域命名主机。
   - 任何域控制器安装也要求连接至 RID 主机。
   - 如果正在现有林中安装第一个只读域控制器，则需要为每一个应用程序目录分区（也称作非域命名上下文或 NDNC）连接至结构主机。

6. 请确保提供必要的凭据以运行 AD DS 安装。

   |安装操作|凭据要求|
   |-----------------------|---------------------------|
   |安装一个新林|目标服务器上的本地管理员|
   |在现有林中安装一个新域|企业管理员|
   |在现有域中安装另一个 DC|域管理员|
   |运行 adprep /forestprep|Schema Admins、Enterprise Admins 和 Domain Admins|
   |运行 adprep /domainprep|域管理员|
   |运行 adprep /domainprep /gpprep|域管理员|
   |运行 adprep /rodcprep|企业管理员|

   你可以委托权限以安装 AD DS。 有关详细信息，请参阅 [安装管理任务](/previous-versions/windows/it-pro/windows-server-2003/cc773327(v=ws.10))。

下面的链接提供了通过 Windows PowerShell cmdlet 和服务器管理器，提升新的和副本 Windows Server 2012 域控制器的分步式指导说明：

- [安装 Active Directory 域服务（级别 100）](./install-active-directory-domain-services--level-100-.md)
- [安装新的 Windows Server 2012 Active Directory 林（级别 200）](./install-a-new-windows-server-2012-active-directory-forest--level-200-.md)
- [在现有域中安装副本 Windows Server 2012 域控制器（级别 200）](./install-a-replica-windows-server-2012-domain-controller-in-an-existing-domain--level-200-.md)
- [安装新的 Windows Server 2012 Active Directory 子域或树域（级别 200）](./install-a-new-windows-server-2012-active-directory-child-or-tree-domain--level-200-.md)
- [安装 Windows Server 2012 Active Directory 只读域控制器 (RODC)（级别 200）](./rodc/install-a-windows-server-2012-active-directory-read-only-domain-controller--rodc---level-200-.md)
- [Windows Server 2012 论坛关于域控制器](/answers/topics/windows-server-2012.html)

## <a name="windows-update-considerations"></a>Windows 更新注意事项

在 Windows 8 发布前，Windows 更新曾管理自己的内部计划以检查更新，并下载和安装它们。 它要求 Windows 更新代理始终在后台运行，这会消耗内存和其他系统资源。

Windows 8 和 Windows Server 2012 引入了一种名为 [自动维护](/windows/win32/w8cookbook/automatic-maintenance)的新功能。 自动维护整合了许多不同的功能，每个都曾用于管理自身的计划和执行逻辑。 这种整合允许所有这些组件使用更少的系统资源、持续工作、遵守新设备类型的新 [连接待机](/windows/win32/w8cookbook/automatic-maintenance) 状态，并在便携设备上消耗更少的电量。

由于 Windows 更新是 Windows 8 和 Windows Server 2012 中的自动维护的一部分，因此它自身内部用于设置日期和时间以安装更新的计划不再有效。 要帮助确保企业中的所有设备和计算机的重新启动行为一致且可预测（包括运行 Windows 8 和 Windows Server 2012 的设备和计算机），请参阅 Microsoft 知识库文章 [2885694](https://support.microsoft.com/kb/2885694) （或参阅 2013 年 10 月累积汇总 [2883201](https://support.microsoft.com/kb/2883201)），然后配置 WSUS 博客文章 [使 Windows 8 和 Windows Server 2012 的 Windows 更新体验更可预测 (KB 2885694)](/archive/blogs/wsus/enabling-a-more-predictable-windows-update-experience-for-windows-8-and-windows-server-2012-kb-2885694)中描述的策略设置。

## <a name="whats-new-in-ad-ds-in-windows-server-2012-r2"></a><a name="BKMK_NewWS2012R2"></a>Windows Server 2012 R2 中 AD DS 有哪些新功能？

下表概述了 Windows Server 2012 R2 中的 AD DS 的新增功能，并提供关于其适用情况的更详细信息的链接。 有关某些功能的更为详细的解释（包括其要求），请参阅 [Windows Server 2012 R2 中的 Active Directory 的新增功能](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn268294(v=ws.11))。

|功能|说明|
|-----------|---------------|
|[工作区加入](../../ad-fs/operations/join-to-workplace-from-any-device-for-sso-and-seamless-second-factor-authentication-across-company-applications.md)|使信息工作人员可以将其个人设备加入他们的公司，以访问公司资源和服务。|
|[Web 应用程序代理](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn280942(v=ws.11))|使用新的远程访问角色服务提供对 Web 应用程序的访问权限。|
|[Active Directory 联合身份验证服务](../../active-directory-federation-services.md)|AD FS 具有简化的部署和改进功能，以使用户可以从个人设备访问资源，并帮助 IT 部门管理访问控制。|
|[SPN 和 UPN 唯一性](../manage/component-updates/spn-and-upn-uniqueness.md)|运行 Windows Server 2012 R2 的域控制器阻止创建重复的服务主体名称 (SPN) 和用户主体名称 (UPN)。|
|[Winlogon 自动重启登录 (ARSO)](../manage/component-updates/winlogon-automatic-restart-sign-on--arso-.md)|使锁屏应用程序可重新启动并在 Windows 8.1 设备上可用。|
|[TPM 密钥证明](../manage/component-updates/tpm-key-attestation.md)|使 CA 可以在颁发的证书中以加密方式证明证书申请者私钥实际上由受信任的平台模块 (TPM) 保护。|
|[凭据保护和管理](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn408190(v=ws.11))|用于减少凭据被盗的新凭据保护和域身份验证控件。|
|[文件复制服务 (FRS) 已弃用](../manage/component-updates/directory-services-component-updates.md)|还弃用 Windows Server 2003 域功能级别，因为在该功能级别上，FRS 用于复制 SYSVOL。 这意味着，当你在运行 Windows Server 2012 R2 的服务器上创建新域时，域功能级别必须是 Windows Server 2008 或更新版本。 你仍可以将运行 Windows Server 2012 R2 的域控制器添加到具有 Windows Server 2003 域功能级别的现有域;你不能在该级别创建新域。|
|[新的域和林功能级别](../active-directory-functional-levels.md)|Windows Server 2012 R2 具有新的功能级别。 Windows Server 2012 R2 DFL 上提供新功能。|
|[LDAP 查询优化程序更改](../manage/component-updates/directory-services-component-updates.md)|对复杂查询的 LDAP 搜索效率和 LDAP 搜索时间进行了性能改进。|
|[1644 事件改进](../manage/component-updates/directory-services-component-updates.md)|LDAP 搜索结果统计信息已添加到事件 ID 1644 以帮助解决疑难问题。|
|[Active Directory 复制吞吐量改进](../manage/component-updates/directory-services-component-updates.md)|将最大 AD 复制吞吐量从 40Mbps 调整到 600 Mbps 左右|

## <a name="whats-new-in-ad-ds-in-windows-server-2012"></a><a name="BKMK_WhatsNewAD"></a>Windows Server 2012 中 AD DS 有哪些新功能？

下表概述了 Windows Server 2012 中的 AD DS 的新增功能，并提供关于其适用情况的更详细信息的链接。 有关某些功能的更多详细说明（包括其要求），请参阅 [AD DS) 中 Active Directory 域服务 (的新增 ](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831477(v=ws.11))功能。

|功能|说明|
|-----------|---------------|
|基于 Active Directory 的激活 (AD BA)；请参阅 [批量激活概述](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831612(v=ws.11))|可以简化配置分发的任务及批量软件许可证的管理。|
|[Active Directory 联合身份验证服务 (AD FS)](../../active-directory-federation-services.md)|增加了通过服务器管理器安装角色、简化的信任设置、自动的信任管理、支持 SAML 协议等。|
|Active Directory 丢失的页面刷新事件|记录带有 jet 错误 1119 的 NTDS ISAM 事件 530，以便检测有无 Active Directory 数据库的丢失页面刷新事件。|
|[Active Directory 回收站用户界面](../get-started/adac/introduction-to-active-directory-administrative-center-enhancements--level-100-.md#ad_recycle_bin_mgmt)|Active Directory 管理中心 (ADAC) 新增了回收站功能（这项功能最初在 Windows Server 2008 R2 中引入）的图形用户界面 (GUI) 管理。|
|[使用 Windows PowerShell cmdlet 进行 Active Directory 复制和拓扑管理](../manage/powershell/introduction-to-active-directory-replication-and-topology-management-using-windows-powershell--level-100-.md)|支持使用 Windows PowerShell 创建和管理 Active Directory 站点、站点链接、连接对象等。|
|[动态访问控制](../../solution-guides/dynamic-access-control--scenario-overview.md)|新增基于声明的授权平台，可以改进旧的访问控制模型。|
|[细化的密码策略用户界面](../get-started/adac/introduction-to-active-directory-administrative-center-enhancements--level-100-.md#fine_grained_pswd_policy_mgmt)|ADAC 新增了 GUI 支持，可用于创建、编辑和分配最初在 Windows Server 2008 中加入的 PSO。|
|[组托管服务帐户 (gMSA)](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831782(v=ws.11))|一种称作 gMSA 的新安全主体类型。 可以使用相同的 gMSA 帐户在多台主机上运行各种服务。|
|[DirectAccess 脱机加入域](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574150(v=ws.11))|可以通过包含 DirectAccess 先决条件，扩展脱机加入域。|
|[通过虚拟化域控制器 (DC) 克隆快速部署](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574150(v=ws.11)#virtualized_dc_cloning)|通过使用 Windows PowerShell cmdlet 克隆现有的虚拟化域控制器，可以快速部署虚拟化 DC。|
|[RID 池大小的更改](../manage/managing-rid-issuance.md)|添加新的监视事件及配额，防止过度消耗全局 RID 池。 如果最初的全局 RID 池已经用完，则可以选择将池的大小扩大一倍。|
|安全的时间服务|通过在线删除机密、删除 MD5 哈希函数并要求服务器使用 Windows 8 时间客户端进行身份验证，可以提高 W32tm 的安全性|
|[虚拟化 DC 的 USN 回滚保护](../manage/managing-rid-issuance.md)|意外还原虚拟化 DC 的快照备份将不再会导致 USN 回滚。|
|[Windows PowerShell 历史记录查看器](../get-started/adac/introduction-to-active-directory-administrative-center-enhancements--level-100-.md#windows_powershell_history_viewer)|允许管理员查看在使用 ADAC 时执行的 Windows PowerShell 命令。|

### <a name="automatic-maintenance-and-changes-to-restart-behavior-after-updates-are-applied-by-windows-update"></a><a name="BKMK_"></a>在 Windows 更新应用更新后的自动维护和对重新启动行为的更改

在 Windows 8 发布前，Windows 更新曾管理自己的内部计划以检查更新，并下载和安装它们。 它要求 Windows 更新代理始终在后台运行，这会消耗内存和其他系统资源。

Windows 8 和 Windows Server 2012 引入了一种名为 [自动维护](/windows/win32/w8cookbook/automatic-maintenance)的新功能。 自动维护整合了许多不同的功能，每个都曾用于管理自身的计划和执行逻辑。 这种整合允许所有这些组件使用更少的系统资源、持续工作、遵守新设备类型的新 [连接待机](/windows/win32/w8cookbook/automatic-maintenance) 状态，并在便携设备上消耗更少的电量。

由于 Windows 更新是 Windows 8 和 Windows Server 2012 中的自动维护的一部分，因此它自身内部用于设置日期和时间以安装更新的计划不再有效。 若要帮助企业中所有设备和计算机确保一致且可预测的重新启动行为（包括那些运行 Windows 8 和 Windows Server 2012 的计算机），你可以配置以下组策略设置：

- **计算机配置|策略|管理模板|Windows 组件|Windows 更新|配置自动更新**
- **计算机配置|策略|管理模板|Windows 组件|Windows 更新|不为登录的用户自动重新启动**
- **计算机配置|策略|管理模板|Windows 组件|维护计划程序|维护随机延迟**

下表列出了一些如何配置这些设置以提供所需的重新启动行为的示例。

|||
|-|-|
|**方案**|**推荐的配置 () **|
|**由 WSUS 管理**<p>-每周安装一次更新<br />-在晚上11点重新启动星期五|将计算机设置为自动安装，在所需时间之前阻止自动重新启动<p>策略****：配置自动更新（已启用）<p>配置自动更新： 4-自动下载并计划安装<p>**策略**： (禁用已登录用户的自动重新启动) <p>**WSUS 截止时间**：设置为周五晚上 11 点|
|**由 WSUS 管理**<p>-在不同小时/天交错安装|为应该一起更新的计算机的不同组设置目标组<p>为之前的方案使用上述步骤<p>为不同的目标组设置不同的截止时间|
|**非 WSUS 管理-不支持截止时间**<p>-在不同时间交错安装|策略****：配置自动更新（已启用）<p>配置自动更新： 4-自动下载并计划安装<p>**注册表项：** 启用在 Microsoft 知识库文章 [2835627](https://support.microsoft.com/kb/2835627)<p>**策略：** 自动维护随机延迟（已启用）<p>为 6 小时随机延迟将“常规维护随机延迟”**** 设置为 PT6H 以提供以下行为：<p>-将在配置的维护时间和随机延迟安装更新<p>-重新启动每台计算机将在3天后发生<p>此外，为每个计算机组设置不同的维护时间|

有关 Windows 工程团队已实现这些更改的原因的详细信息，请参阅 [在 Windows Update 的自动更新中尽量减少重新启动](https://blogs.msdn.com/b/b8/archive/2011/11/14/minimizing-restarts-after-automatic-updating-in-windows-update.aspx)。

## <a name="ad-ds-server-role-installation-changes"></a><a name="BKMK_InstallationChanges"></a>AD DS 服务器角色安装变更

在 Windows Server 2003 到 Windows Server 2008 R2 版本中，你需要在运行 Active Directory 安装向导 (Dcpromo.exe) 之前，先运行 Adprep.exe 命令行工具的 x86 或 X64 版本，Dcpromo.exe 包含可供选择的变体，既可以从媒体安装，也可以进行无人参与的安装。

从 Windows Server 2012 开始，通过使用 Windows PowerShell 中的 ADDSDeployment 模块执行命令行安装。 基于 GUI 的升级是通过使用全新的 AD DS 配置向导在服务器管理器中执行的。 为了简化安装过程，ADPREP 已经被集成到 AD DS 安装中，并且可以根据需要自动运行。 基于 Windows PowerShell 的 AD DS 配置向导会自动以添加了 Dc 的域中的架构和基础结构主机角色为目标，然后在相关域控制器上远程运行所需的 ADPREP 命令。

AD DS 安装向导中的先决条件检查可以在开始安装之前识别潜在的错误。 错误的条件能够得到纠正以消除仅完成部分升级的顾虑。 该向导还将导出一个 Windows PowerShell 脚本，其中包含图形安装期间指定的所有选项的。

综上所述，AD DS 安装变更简化了 DC 角色的安装过程，减少了出现管理错误的可能性，当你在全局区域和域中部署多个域控制器时尤其如此。
有关 GUI 和基于 Windows PowerShell 的安装的更多详细信息，包括命令行语法以及分步式向导的指导说明，请参阅 [安装 Active Directory 域服务](./install-active-directory-domain-services--level-100-.md)。 如果管理员需要独立于现有林中 Windows Server 2012 DC 安装过程，而控制某个 Active Directory 林中架构变更的引入，则该管理员仍然可以使用提升的命令提示符运行 Adprep.exe 命令。

## <a name="deprecated-features-and-behavior-changes-related-to-ad-ds-in-windows-server-2012"></a><a name="BKMK_DeprecatedFeatures"></a>与 Windows Server 2012 中 AD DS 有关的弃用功能及行为变化

与 AD DS 有关的变化包括：

- **弃用 Adprep32.exe**
   - Adprep.exe 只有一种版本，可以根据需要在运行 Windows Server 2008 或更高版本的 64 位服务器上运行它。 你可以远程运行 Adprep.exe，如果在 32 位操作系统或 Windows Server 2003 上托管目标操作主机角色，则必须远程运行该程序。
- **弃用 Dcpromo.exe**
   - Dcpromo 已弃用，但在 Windows Server 2012 中，它仍可以使用应答文件或命令行参数运行，从而使组织能够时间将现有的自动化转换为新的 Windows PowerShell 安装选项。
- **针对用户帐户禁用 LMHash**
  - Windows Server 2008、Windows Server 2008 R2 和 Windows Server 2012 上安全模板中的安全默认设置均启用了 NoLMHash 策略，而该项策略在 Windows 2000 和 Windows Server 2003 域控制器的安全模板中则是被禁用的。 请参阅知识库文章 [946405](https://support.microsoft.com/kb/946405)中介绍的步骤，按照要求，禁用依赖于 LMHash 客户端的 NoLMHash 策略。

从 Windows Server 2008 开始，域控制器还具有以下安全默认设置，与运行 Windows Server 2003 或 Windows 2000 的域控制器相比。

| 加密类型或策略 | Windows Server 2008 默认设置 | Windows Server 2012 和 Windows Server 2008 R2 默认设置 | 评论 |
|--|--|--|--|
| AllowNT4Crypto | 已禁用 | 已禁用 | 第三方服务器消息块 (SMB) 客户端可能与域控制器上的安全默认设置不兼容。 在所有情况下，可以通过放宽这些设置来允许交互操作，但这终将是以牺牲安全性为代价。 有关详细信息，请参阅 Microsoft 知识库中的 [文章 942564](https://go.microsoft.com/fwlink/?LinkId=164558) (https://go.microsoft.com/fwlink/?LinkId=164558) 。 |
| DES | 已启用 | 已禁用 | Microsoft 知识库中的[文章 977321](https://go.microsoft.com/fwlink/?LinkId=177717) (https://go.microsoft.com/fwlink/?LinkId=177717) |
| 集成身份验证的 CBT/扩展保护 | 不适用 | 已启用 | 请参阅 microsoft 知识库 (中的 [Microsoft 安全公告 (937811) ](https://go.microsoft.com/fwlink/?LinkId=164559) (https://go.microsoft.com/fwlink/?LinkId=164559) 和 [文章 976918](https://go.microsoft.com/fwlink/?LinkId=178251) https://go.microsoft.com/fwlink/?LinkId=178251) 。<p>按照要求，查看并安装 Microsoft 知识库 [文章 977073](https://go.microsoft.com/fwlink/?LinkId=186394) (中的修补程序 https://go.microsoft.com/fwlink/?LinkId=186394) 。 |
| LMv2 | 已启用 | 已禁用 | Microsoft 知识库中的[文章 976918](https://go.microsoft.com/fwlink/?LinkId=178251) (https://go.microsoft.com/fwlink/?LinkId=178251) |

## <a name="operating-system-requirements"></a><a name="BKMK_SysReqs"></a>操作系统要求

下表列出了 Windows Server 2012 的最低系统要求。 有关系统要求的更多信息以及预安装信息，请参阅 [安装 Windows Server 2012](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj134246(v=ws.11))。 安装一个新的 Active Directory 林时，并无其他额外的系统要求。但是为了提高域控制器、LDAP 客户端请求以及启用了 Active Directory 的应用程序的性能，应当增加足够的内存以此来缓存 Active Directory 数据库中的内容。 如果要升级现有域控制器或将新域控制器添加到现有林，请查阅下一部分，以确保服务器满足磁盘空间要求。

| 要求 | 值 |
|--|--|
| 处理器 | 1.4 GHz 64 位处理器 |
| RAM | 512 MB |
| 可用磁盘空间要求 | 32 GB |
| 屏幕分辨率 | 800 x 600 或更高 |
| 杂项 | DVD 驱动器、键盘、Internet 访问权限 |

### <a name="disk-space-requirements-for-upgrading-domain-controllers"></a><a name="BKMK_DiskSpaceDCWin8"></a>升级域控制器的磁盘空间要求

本部分介绍仅用于从 Windows Server 2008 或 Windows Server 2008 R2 升级域控制器的磁盘空间要求。 有关将域控制器升级到早期版本的 Windows Server 的磁盘空间要求的详细信息，请参阅 [升级到 Windows Server 2008 的磁盘空间要求](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754463(v=ws.10)#BKMK_2008) 或 [升级到 Windows Server 2008 R2 的磁盘空间要求](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754463(v=ws.10)#BKMK_2008R2)。

为了容纳自定义的和应用程序驱动的架构扩展、应用程序以及管理员启动的索引，需要向托管 Active Directory 数据库和日志文件的磁盘分配空间；此外，还需要为部署域控制器期间（通常为 5 至 8 年）添加到目录中的对象和属性提供空间。 在部署时就分配适当的磁盘空间通常是一项可靠的投资，相比较而言，如果完成部署后再扩展磁盘存储空间，则需要花费更多的成本。 有关详细信息，请参阅 [Active Directory 域服务的容量规划](../../../administration/performance-tuning/role/active-directory-server/capacity-planning-for-active-directory-domain-services.md)。

在计划升级的域控制器上，请在开始升级操作系统之前，先确保托管 Active Directory 数据库 (NTDS.DIT) 的驱动器至少具有相当于 NTDS.DIT 文件大小 20% 的可用磁盘空间。 如果卷上没有足够的可用磁盘空间，升级将会失败并且升级兼容性报告将返回错误，指明可用磁盘空间不足：

在这种情况下，可以尝试 Active Directory 数据库的脱机碎片整理，以重新获得附加空间，然后重试升级。 有关详细信息，请参阅 [压缩目录数据库文件（脱机碎片整理）](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794920(v=ws.10))。

### <a name="available-skus"></a>可用的 SKU

有 4 个版本的 Windows Server：Foundation、Essentials、Standard 和 Datacenter。
其中，支持 AD DS 角色的两种版本分别是 Standard 和 Datacenter。

在以前的发行版本中，Windows Server 各个版本在其服务器角色的支持方面、处理器计数以及大量内存支持方面均有不同。 Windows Server 的 Standard 和 Datacenter 版本支持所有功能和基础硬件，但其虚拟化权限不同-标准版允许两个虚拟实例，而 Datacenter edition 允许使用无限制的虚拟实例。

### <a name="windows-client-and-windows-server-operating-systems-that-are-supported-to-join-windows-server-domains"></a>支持加入 Windows Server 域的 Windows 客户端和 Windows Server 操作系统

具有运行 Windows Server 2012 或更高版本的域控制器的域成员计算机支持下列 Windows 客户端和 Windows Server 操作系统：

- 服务器操作系统：Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008、Windows Server 2003 R2、Windows Server 2003

## <a name="supported-in-place-upgrade-paths"></a><a name="BKMK_UpgradePaths"></a>支持的就地升级路径

运行64位版本的 Windows Server 2008 或 Windows Server 2008 R2 的域控制器可以升级到 Windows Server 2012。 运行 Windows Server 2003 或 Windows Server 2008 32 位版本的域控制器则无法升级。 若要替换它们，请在域中安装运行更新版本的 Windows Server 的域控制器，然后删除运行 Windows Server 2003 的域控制器。

| 如果运行下列版本 | 可以升级到这些版本 |
|--|--|
| 带有 SP2 的 Windows Server 2008 Standard<p>要么<p>带有 SP2 的 Windows Server 2008 Enterprise | Windows Server 2012 Standard<p>要么<p>Windows Server 2012 Datacenter |
| 带有 SP2 的 Windows Server 2008 Datacenter | Windows Server 2012 Datacenter |
| Windows Web Server 2008 | Windows Server 2012 Standard |
| 带有 SP1 的 Windows Server 2008 R2 Standard<p>要么<p>带有 SP1 的 Windows Server 2008 R2 Enterprise | Windows Server 2012 Standard<p>要么<p>Windows Server 2012 Datacenter |
| 带有 SP1 的 Windows Server 2008 R2 Datacenter | Windows Server 2012 Datacenter |
| Windows Web Server 2008 R2 | Windows Server 2012 Standard |

有关支持的升级路径的详细信息，请参阅 [Windows Server 2012 的评估版本和升级选项](https://go.microsoft.com/fwlink/?LinkId=260917)。 注意：你无法将运行 Windows Server 2012 评估版的域控制器直接转换为零售版本。 相反，应该在服务器上安装另一个运行零售版本的域控制器，并从运行评估版的域控制器中删除 AD DS。

由于已知问题，你无法将运行 Windows Server 2008 R2 的服务器核心安装的域控制器升级到 Windows Server 2012 的服务器核心安装。 在升级过程的后期，升级将会终止，彻底黑屏。 如果重新启动此类 DC，则会显示 boot.ini 文件中的一个选项，允许回滚到以前的操作系统版本。 再次重新启动将触发系统自动回滚到以前的操作系统版本。 在解决方案可用之前，建议安装新的域控制器运行 Windows Server 2012 的服务器核心安装，而不是就地升级运行 Windows Server 2008 R2 的服务器核心安装的现有域控制器。 有关详细信息，请参阅知识库文章 [2734222](https://support.microsoft.com/kb/2734222)。

## <a name="functional-level-features-and-requirements"></a><a name="BKMK_FunctionalLevels"></a>功能级别的功能和要求

Windows Server 2012 需要 Windows Server 2003 林功能级别。 也就是说，在将运行 Windows Server 2012 的域控制器添加到现有 Active Directory 林之前，林功能级别必须是 Windows Server 2003 或更高版本。 这意味着运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的域控制器可以在同一个林中操作，但是不支持运行 Windows 2000 Server 的域控制器，而且它会阻止安装运行 Windows Server 2012 的域控制器。 如果林包含运行 Windows Server 2003 或更高版本的域控制器，但是域功能级别仍是 Windows 2000，则安装也会被阻止。

在将 Windows Server 2012 域控制器添加到林之前，必须先删除 Windows 2000 域控制器。 对于这种情况，请考虑下列工作流：

1. 安装运行 Windows Server 2003 或更高版本的域控制器。 这些域控制器可以部署在 Windows Server 的评估版上。 作为先决条件，该步骤还要求为此操作系统版本 [运行 adprep.exe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd464018(v=ws.10)) 。
2. 删除 Windows 2000 域控制器。 具体来说，从域中适当降级或强制性删除 Windows Server 2000 域控制器，并且使用“Active Directory 用户和计算机”，将所有已删除的域控制器的域控制器帐户删除。
3. 将林功能级别提升到 Windows Server 2003 或更高版本。
4. 安装运行 Windows Server 2012 的域控制器。
5. 删除运行 Windows Server 早期版本的域控制器。

新的 Windows Server 2012 域功能级别启用一个新功能： " **KDC 支持声明、复合身份验证和 Kerberos** 保护" kdc 管理模板策略具有两个设置 (**始终提供** 要求 Windows Server 2012 域功能级别) 的声明和 **未保护身份验证请求** 。

Windows Server 2012 林功能级别不提供任何新功能，但可确保在林中创建的任何新域都将在 Windows Server 2012 域功能级别上自动运行。 Windows Server 2012 域功能级别不提供 KDC 支持声明、复合身份验证和 Kerberos 保护之外的其他新功能。 但它会确保域中的任何域控制器都运行 Windows Server 2012。 有关不同功能级别提供的其他功能的详细信息，请参阅 [了解 Active Directory 域服务 (AD DS) 功能级别](../active-directory-functional-levels.md)。

将林功能级别设置为某个值之后，就不能回滚或降低林功能级别，但有以下例外：将林功能级别提升到 Windows Server 2012 后，可以将其降低到 Windows Server 2008 R2。 如果尚未启用 Active Directory 回收站，还可以将林功能级别从 Windows Server 2012 降级到 Windows Server 2008 R2 或 Windows server 2008 或从 Windows Server 2008 R2 降低为 Windows Server 2008。 例如，如果将林功能级别设置为 Windows Server 2008 R2，则无法将其回滚到 Windows Server 2003。

将域功能级别设置为特定值后，你不能回滚或降低域功能级别，但以下情况例外：当你将域功能级别提升到 Windows Server 2008 R2 或 Windows Server 2012 时，如果林功能级别为 Windows Server 2008 或更低，则可以选择将域功能级别回滚到 Windows Server 2008 或 Windows Server 2008 R2。 只能将域功能级别从 Windows Server 2012 降级到 Windows Server 2008 R2 或 Windows server 2008 或从 Windows Server 2008 R2 降低到 Windows Server 2008。 如果域功能级别设置为 Windows Server 2008 R2，则无法将其回滚到 Windows Server 2003。

有关较低功能级别提供的功能的详细信息，请参阅 [了解 Active Directory 域服务 (AD DS) 功能级别](../active-directory-functional-levels.md)。

除了功能级别以外，运行 Windows Server 2012 的域控制器还提供运行早期版本 Windows Server 的域控制器上不可用的其他功能。 例如，运行 Windows Server 2012 的域控制器可用于虚拟域控制器克隆，而运行早期版本 Windows Server 的域控制器则不能。 但 Windows Server 2012 中的虚拟域控制器克隆和虚拟域控制器保护不具有任何功能级别要求。

> [!NOTE]
> Microsoft Exchange Server 2013 要求林功能级别为 Windows server 2003 或更高版本。

## <a name="ad-ds-interoperability-with-other-server-roles-and-windows-operating-systems"></a><a name="BKMK_ServerRoles"></a>AD DS 与其他服务器角色及 Windows 操作系统的互操作性

下列 Windows 操作系统不支持 AD DS：

- Windows MultiPoint Server
- Windows Server 2012 Essentials

无法将 AD DS 安装在同时运行下列服务器角色或角色服务的服务器上：

- Hyper-V Server
- 远程桌面连接代理

## <a name="operations-master-roles"></a><a name="BKMK_OpsMasters"></a>操作主机角色

Windows Server 2012 中的一些新功能影响操作主机角色：

- PDC 仿真器必须运行 Windows Server 2012，以支持克隆虚拟域控制器。 克隆 DC 存在附加先决条件。 有关详细信息，请参阅 [Active Directory 域服务 (AD DS) 虚拟化](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd464018(v=ws.10))。
- PDC 仿真器运行 Windows Server 2012 时，将创建新的安全主体。
- RID 主体具有新 RID 颁发和监视功能。 改进包括更好的事件日志记录、更合适的限制以及在紧急情况下将总体 RID 池分配增加 1 位的功能。 有关详细信息，请参阅[管理 RID 颁发](../../ad-ds/manage/Managing-RID-Issuance.md)。

> [!NOTE]
> 尽管它们不是操作主机角色，但 AD DS 安装中的另一项更改是：默认情况下，在运行 Windows Server 2012 的所有域控制器上安装 DNS 服务器角色和全局编录。

## <a name="virtualizing-domain-controllers"></a><a name="BKMK_Virtual"></a>虚拟化域控制器

从 Windows Server 2012 开始 AD DS 改进使域控制器的虚拟化和克隆域控制器的能力更安全。 而克隆域控制器又支持在新域中快速部署其他域控制器和其他好处。 有关详细信息，请参阅 [Active Directory 域服务 &#40;的简介 AD DS&#41; 虚拟化 &#40;级别 100&#41;](../../ad-ds/Introduction-to-Active-Directory-Domain-Services-AD-DS-Virtualization-Level-100.md)。

## <a name="administration-of-windows-server-2012-servers"></a><a name="BKMK_Admin"></a>管理 Windows Server 2012 服务器

使用 [适用于 windows 8 的远程服务器管理工具](https://www.microsoft.com/download/details.aspx?id=28972) 来管理运行 windows Server 2012 的域控制器和其他服务器。 可以在运行 Windows 8 的计算机上运行 Windows Server 2012 远程服务器管理工具。

## <a name="application-compatibility"></a><a name="BKMK_AppCompat"></a>应用程序兼容性

下表包含了常见的集成 Active Directory 的 Microsoft 应用程序。 下表列出了可安装应用程序的 Windows Server 版本以及引入 Windows Server 2012 DC 是否会影响应用程序的兼容性。

|产品|说明|
|-----------|---------|
|[Microsoft SharePoint 2010](https://support.microsoft.com/kb/2724471)|在 Windows Server 2012 服务器上安装和操作 SharePoint 2010 时， <br />要求提供 SharePoint 2010 Service Pack 2<p>在 Windows Server 2012 服务器上安装和操作 SharePoint 2010 Foundation 时，要求提供 SharePoint 2010 Foundation Service Pack 2<p>无法在 Windows Server 2012 上安装 SharePoint Server 2010（没有 Service Pack）<p>SharePoint Server 2010 必备安装程序 ( # A0) 失败，并出现错误 "此程序存在兼容性问题。" 单击 "运行程序而不获取帮助" 将显示错误 "验证是否可以安装 SharePoint Server 2010 (&#124; 没有 service pack) 无法在 Windows Server 2012 上安装。"|
|[Microsoft SharePoint 2013](/SharePoint/install/hardware-and-software-requirements-0)|针对服务器场中数据库服务器的最低要求：<p>Windows Server 2008 R2 Service Pack 1 (SP1) Standard、Enterprise 或 Datacenter 的 64 位版本，或者 Windows Server 2012 Standard 或 Datacenter 的 64 位版本<p>针对带有内置数据库的单个服务器的最低要求：<p>Windows Server 2008 R2 Service Pack 1 (SP1) Standard、Enterprise 或 Datacenter 的 64 位版本，或者 Windows Server 2012 Standard 或 Datacenter 的 64 位版本<p>针对服务器场中前端 Web 服务器和应用程序服务器的最低要求：<p>Windows Server 2008 R2 Service Pack 1 (SP1) Standard、Enterprise 或 Datacenter 的 64 位版本，或者 Windows Server 2012 Standard 或 Datacenter 的 64 位版本。|
|[Configuration Manager 2012](/SharePoint/install/hardware-and-software-requirements-0)|Configuration Manager 2012 Service Pack 1：<p>随着 Service Pack 1 的发布，Microsoft 将会向我们的客户端支持矩阵添加下列操作系统：<p>-Windows 8 专业版<br />-Windows 8 企业版<br />-Windows Server 2012 标准版<br />-Windows Server 2012 Datacenter<p>可以将所有站点服务器角色 - 包括站点服务器、SMS 提供程序以及管理点 - 部署到具有下列操作系统版本的服务器中：<p>-Windows Server 2012 标准版<br />-Windows Server 2012 Datacenter|
|[Microsoft 端点 Configuration Manager (当前分支) ](/configmgr/core/plan-design/configs/supported-configurations)|[Configuration Manager 的站点系统服务器支持的操作系统](/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers)。|
|[Microsoft Lync Server 2013](/lyncserver/lync-server-2013-server-and-tools-operating-system-support)|Lync Server 2013 要求与 Windows Server 2008 R2 或 Windows Server 2012 一起使用。 它无法运行在服务器核心安装上。 它可以运行在 [虚拟服务器](/lyncserver/lync-server-2013-running-lync-server-on-virtual-servers)上。|
|[Lync Server 2010](https://support.microsoft.com/kb/2777359)|如果安装了 [Lync Server 2012 年 10 月的累计更新](https://support.microsoft.com/?kbid=2493736) ，则可以将 Lync Server 2010 安装到全新（并非升级）的 Windows Server 2012 安装中。 不支持针对现有的 Lync Server 2010 安装，将操作系统升级至 Windows Server 2012。 此外，Windows Server 2012 上也不支持 Microsoft Lync Server 2010 群聊服务器。|
|[System Center 2012 Endpoint Protection](/SharePoint/install/hardware-and-software-requirements-0)|System Center 2012 Endpoint Protection Service Pack 1 将更新客户端支持矩阵以包含下列操作系统：<p>-Windows 8 专业版<br />-Windows 8 企业版<br />-Windows Server 2012 标准版<br />-Windows Server 2012 Datacenter|
|[System Center 2012 Forefront Endpoint Protection](/SharePoint/install/hardware-and-software-requirements-0)|FEP 2010 更新汇总 1 将更新客户端支持矩阵以包括下列操作系统：<p>-Windows 8 专业版<br />-Windows 8 企业版<br />-Windows Server 2012 标准版<br />-Windows Server 2012 Datacenter|
|Forefront Threat Management Gateway (TMG)|只支持 TMG 在 Windows Server 2008 和 Windows Server 2008 R2 上运行。 有关详细信息，请参阅 [Forefront TMG 系统要求](/previous-versions/tn-archive/dd896981(v=technet.10))。|
|Windows Server 更新服务|此版本的 WSUS 已经支持基于 Windows 8 的计算机或支持基于 Windows Server 2012 的计算机作为客户端。|
|Windows Server Update Services 3.0|更新知识库文章 [2734608](https://support.microsoft.com/kb/2734608) 允许运行 WINDOWS SERVER UPDATE SERVICES (WSUS) 3.0 SP2 的服务器为运行 Windows 8 或 Windows Server 2012 的计算机提供更新： **注意：** 具有独立 wsus 3.0 SP2 环境的客户或 Configuration Manager 2007 Service Pack 2 环境（含 WSUS 3.0 SP2）需要 [2734608](https://support.microsoft.com/kb/2734608) 来正确地将基于 Windows 8 的计算机或基于 windows Server 2012 的计算机作为客户端进行管理。|
|[Exchange 2013](/Exchange/plan-and-deploy/prerequisites?view=exchserver-2019)|下列服务器角色支持 Windows Server 2012 Standard 和 Datacenter：架构主机、全局编录服务器、域控制器、邮箱和客户端访问服务器角色<p>林功能级别：Windows Server 2003 或更高版本<p>源：Exchange 2013 系统要求|
|Exchange 2010|[源：Exchange 2010 Service Pack 3](https://techcommunity.microsoft.com/t5/exchange-team-blog/bg-p/Exchange)<p>可以在 Windows Server 2012 成员服务器上安装带有 Service Pack 3 的 Exchange 2010。<p>对于 Windows Server 2008 R2，[Exchange 2010 系统要求](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141)) 列出了最新支持的架构主机、全局编录服务器和域控制器。<p>林功能级别：Windows Server 2003 或更高版本|
|SQL Server 2012|源：KB [2681562](https://support.microsoft.com/kb/2681562)<p>Windows Server 2012 上支持 SQL Server 2012 RTM。|
|SQL Server 2008 R2|源：KB [2681562](https://support.microsoft.com/kb/2681562)<p>要求在 Windows Server 2012 上安装带有 Service Pack 1 的 SQL Server 2008 R2 或更高版本。|
|SQL Server 2008|源：KB [2681562](https://support.microsoft.com/kb/2681562)<p>要求在 Windows Server 2012 上安装带有 Service Pack 3 的 SQL Server 2008 或更高版本。|
|SQL Server 2005|源：KB [2681562](https://support.microsoft.com/kb/2681562)<p>不支持在 Windows Server 2012 上进行安装。|

## <a name="known-issues"></a><a name="BKMK_KnownIssues"></a>已知问题

下表列出了与 AD DS 安装有关的已知问题。

| 知识库文章编号及标题 | 影响的技术区域 | 问题/描述 |
|--|--|--|
| [2830145](https://support.microsoft.com/kb/2830145)：在域环境中，SID S-1-18-1 和 SID S-1-18-2 无法映射到基于 Windows 7 或 Windows Server 2008 R2 的计算机上 | AD DS 管理/应用兼容 | 映射 SID S-1-18-1 和 SID S-1-18-2 的应用程序（Windows Server 2012 中的新增应用程序）可能失败，因为 SID 无法在基于 Windows 7 或基于 Windows Server 2008 R2 的计算机上解析。 若要解决此问题，请在域中基于 Windows 7 和 Windows Server 2008 R2 的计算机上安装修补程序。 |
| [2737129](https://support.microsoft.com/kb/2737129)：当你为 Windows Server 2012 自动准备现有域时，不执行组策略准备 | AD DS 安装 | 作为在域中安装第一个运行 Windows Server 2012 的 DC 的一部分，Adprep /domainprep /gpprep 不会自动运行。 如果以前从未在域中运行它，则必须对它进行手动运行。 |
| [2737416](https://support.microsoft.com/kb/2737416)：基于 Windows PowerShell 的域控制器部署将重复警告 | AD DS 安装 | 警告不仅会在先决条件验证期间出现，而且还会在安装期间重复出现。 |
| [2737424](https://support.microsoft.com/kb/2737424)：当你尝试从域控制器删除 Active Directory 域服务时，出现“指定域名的格式无效”错误 | AD DS 安装 | 当域中仍存在预创建的 RODC 帐户时，如果删除域中最后一个 DC，则会显示此错误。 这会影响 Windows Server 2012、 Windows Server 2008 R2 和 Windows Server 2008。 |
| [2737463](https://support.microsoft.com/kb/2737463)：域控制器不启动、发生 c00002e2 错误或显示“选择一个选项” | AD DS 安装 | 没有启动 DC 是因为管理员使用了 Dism.exe、Pkgmgr.exe 或 Ocsetup.exe 来删除 DirectoryServices-DomainController 角色。 |
| [2737516](https://support.microsoft.com/kb/2737516)：Windows Server 2012 服务器管理器中的 IFM 验证限制 | AD DS 安装 | 如知识库文章中所述，IFM 验证可能存在限制。 |
| [2737535](https://support.microsoft.com/kb/2737535)：Install-addsdomaincontroller cmdlet 返回 RODC 的参数集错误 | AD DS 安装 | 当你尝试将服务器与 RODC 帐户关联时，如果指定的实际参数已经填充到预创建的 RODC 帐户中，则会收到一个错误消息。 |
| [2737560](https://support.microsoft.com/kb/2737560)：“无法执行 Exchange 架构冲突检查”错误，而且先决条件检查失败 | AD DS 安装 | 当你在现有域中配置第一个 Windows Server 2012 DC 时，先决条件检查失败。这是因为 DC 缺少网络服务的 SeServiceLogonRight，或者是因为 WMI 或 DCOM 协议被阻止。 |
| [2737797](https://support.microsoft.com/kb/2737797)：带有 -Whatif 参数的 AddsDeployment 模块显示不正确的 DNS 结果 | AD DS 安装 | -WhatIf 参数显示将不安装 DNS 服务器，但该服务器为。 |
| [2737807](https://support.microsoft.com/kb/2737807)：“域控制器选项”页上不提供“下一步”按钮 | AD DS 安装 | “域控制器选项”页面上的“下一步”按钮被禁用是因为目标 DC 的 IP 地址没有映射到现有子网或站点，或者是因为没有正确键入或确认 DSRM 密码。 |
| [2737935](https://support.microsoft.com/kb/2737935)：Active Directory 安装停留在“正在创建 NTDS 设置对象”阶段 | AD DS 安装 | 安装挂起是因为本地管理员密码匹配域管理员密码，或者是因为网络问题阻止完成关键复制。 |
| [2738060](https://support.microsoft.com/kb/2738060)：当你使用 Install-AddsDomain 远程创建子域时，显示“访问被拒绝”错误消息 | AD DS 安装 | 使用 Invoke-Command cmdlet 运行 Install-ADDSDomain 时，如果 DNSDelegationCredential 有一个错误的密码，则会收到此错误。 |
| [2738697](https://support.microsoft.com/kb/2738697)：通过服务器管理器配置服务器时，出现“服务器不可操作”域控制器配置错误 | AD DS 安装 | 尝试在工作组计算机上安装 AD DS 时会收到此错误，因为 NTLM 身份验证被禁用。 |
| [2738746](https://support.microsoft.com/kb/2738746)：登录到本地管理员域帐户后，收到访问被拒绝错误 | AD DS 安装 | 如果你使用本地管理员帐户而不是内置的管理员帐户登录，然后创建新域，则该帐户将不会添加到 Domain Admins 组中。 |
| [2743345](https://support.microsoft.com/kb/2743345)：“系统找不到指定的文件”Adprep /gpprep 错误或工具故障 | AD DS 安装 | 运行 adprep /gpprep 时会收到此错误，因为结构主机正在实现一个非连续命名空间 |
| [2743367](https://support.microsoft.com/kb/2743367)：在 64 位版本的 Windows Server 2003 上出现 Adprep“不是有效的 Win32 应用程序”错误 | AD DS 安装 | 收到此错误是因为 Windows Server 2012 Adprep 无法在 Windows Server 2003 上运行。 |
| [2753560](https://support.microsoft.com/kb/2753560)：在 Windows Server 2012 上出现 ADMT 3.2 和 PES 3.1 安装错误 | ADMT | 根据设计，无法在 Windows Server 2012 上安装 ADMT 3.2。 |
| [2750857](https://support.microsoft.com/kb/2750857)：DFS 复制诊断报告不能在 Internet Explorer 10 中正确显示 | DFS 复制 | 由于 Internet Explorer 10 中的变化，无法正确显示 DFS 复制诊断报告。 |
| [2741537](https://support.microsoft.com/kb/2741537)：用户可以看到远程组策略更新 | 组策略 | 这是因为计划任务运行在每个登录用户的上下文中。 Windows 任务计划程序设计要求在此方案中出现一个交互式提示。 |
| [2741591](https://support.microsoft.com/kb/2741591)：在 GPMC 基础结构状态选项的 SYSVOL 中未显示 ADM 文件 | 组策略 | 因为 GPMC 基础结构状态未遵循自定义的筛选规则，GP 复制可以报告 "正在进行复制"。 |
| [2737880](https://support.microsoft.com/kb/2737880)：配置 AD DS 期间出现“无法启动服务”错误 | 虚拟 DC 克隆 | 当安装或删除 AD DS，或者克隆 AD DS 时，会收到此错误，因为 DS 角色服务器服务已被禁用。 |
| [2742836](https://support.microsoft.com/kb/2742836)：使用 VDC 克隆功能时，为每个域控制器创建了两个 DHCP 租约 | 虚拟 DC 克隆 | 出现这种情况是因为在克隆之前，克隆的域控制器收到一个租约，而且在克隆结束时，又收到了一个租约。 |
| [2742844](https://support.microsoft.com/kb/2742844)：域控制器克隆失败，服务器在 Windows Server 2012 中以 DSRM 模式重新启动 | 虚拟 DC 克隆 | 由于克隆因知识库文章中所列的任意原因而失败，所以克隆的 DC 以 DSRM 模式启动。 |
| [2742874](https://support.microsoft.com/kb/2742874)：域控制器克隆不会重新创建所有服务主体名称 | 虚拟 DC 克隆 | 因为域重命名过程中的限制，克隆后的 DC 上没有重新创建某些由三部分构成的 SPN。 |
| [2742908](https://support.microsoft.com/kb/2742908)：克隆域控制器后出现“无可用登录服务”错误 | 虚拟 DC 克隆 | 当你在克隆虚拟化的 DC 后尝试登录时，会收到此错误，这是因为克隆失败并且 DC 是以 DSRM 模式启动的。 以管理员身份登录时可以解决此克隆故障。 |
| [2742916](https://support.microsoft.com/kb/2742916)：域控制器克隆失败，dcpromo.log 中出现错误 8610 | 虚拟 DC 克隆 | 克隆失败，因为 PDC 仿真器未曾执行域分区的入站复制，这可能是由于角色传送造成的。 |
| [2742927](https://support.microsoft.com/kb/2742927)：“索引超出范围”New-AdDcCloneConfig 错误 | 虚拟 DC 克隆 | 在克隆虚拟 DC 期间，当运行 New-ADDCCloneConfigFile cmdlet 后会收到此错误，这可能是因为没有从提升的命令提示符中运行该 cmdlet，或者是因为你的访问令牌不包含管理员组。 |
| [2742959](https://support.microsoft.com/kb/2742959)：域控制器克隆失败，出现错误 8437：“为这个复制操作指定了一个无效的参数” | 虚拟 DC 克隆 | 克隆失败，因为指定了无效的克隆名称或重复的 NetBIOS 名称。 |
| [2742970](https://support.microsoft.com/kb/2742970)：DC 克隆失败，没有 DSRM、重复的源和克隆计算机 | 虚拟 DC 克隆 | 克隆后的虚拟 DC 使用重复名称作为源 DC，以目录服务修复模式 (DSRM) 启动，这是因为没有在正确的位置创建 DCCloneConfig.xml 文件，或者因为源 DC 在克隆前已经重新启动。 |
| [2743278](https://support.microsoft.com/kb/2743278)：域控制器克隆错误 0x80041005 | 虚拟 DC 克隆 | 克隆后的 DC 以 DSRM 模式启动，因为仅指定了一个 WINS 服务器。 如果指定了任意的 WINS 服务器，则必须同时指定首选的和备用的 WINS 服务器。 |
| [2745013](https://support.microsoft.com/kb/2745013)：如果在 Windows Server 2012 中运行 New-AdDcCloneConfigFile，则会出现“该服务器不可操作”的错误消息 | 虚拟 DC 克隆 | 在运行 New-ADDCCloneConfigFile cmdlet 后会收到此错误，这是因为服务器无法联系全局编录服务器。 |
| [2747974](https://support.microsoft.com/kb/2747974)：域控制器克隆事件 2224 提供了不正确的指导 | 虚拟 DC 克隆 | 事件 ID 2224 错误地指出在克隆之前必须删除托管服务帐户。 必须删除独立的 MSA，然而组 MSA 并不阻止克隆。 |
| [2748266](https://support.microsoft.com/kb/2748266)：在升级到 Windows 8 后，无法解锁 BitLocker 加密的驱动器 | BitLocker | 当你尝试解锁从 Windows 7 升级的计算机上的驱动器时，会收到 "找不到应用程序" 错误。 |

## <a name="see-also"></a>另请参阅

[Windows Server 2012 评估资源](https://www.microsoft.com/en-us/evalcenter/) 
[Windows Server 2012 评估指南](https://download.microsoft.com/download/5/B/2/5B254183-FA53-4317-B577-7561058CEF42/WS%202012%20Evaluation%20Guide.pdf) 
[安装和部署 Windows Server 2012](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831620(v=ws.11))