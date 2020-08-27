---
ms.assetid: 7a7ab95c-9cb3-4a7b-985a-3fc08334cf4f
title: 实现最小特权的管理模型
ms.author: iainfou
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.openlocfilehash: ab4d6f282de88b7d55256ecd3a9ff4a82a7881fb
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88941447"
---
# <a name="implementing-least-privilege-administrative-models"></a>实现最小特权的管理模型

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

以下摘录来自于1999年4月1日发布 [的管理员帐户安全规划指南](/previous-versions/tn-archive/cc162797(v=technet.10))：

> "与安全性相关的大多数培训课程和文档讨论了最低权限原则的实施，但组织很少关注它。 这一原则很简单，并且正确应用它的影响大大提高了您的安全性并降低了您的风险。 该原则规定，所有用户应使用拥有完成当前任务所需的绝对最低权限的用户帐户登录，而不是其他用户帐户。 这样做可以防止恶意代码以及其他攻击。 此原则适用于计算机和这些计算机的用户。
> "此原则的一个原因是，它会强制您进行一些内部研究。 例如，你必须确定计算机或用户真正需要的访问权限，然后实施这些权限。 对于许多组织而言，此任务最初可能看起来就像是一笔工作，但是，成功保护网络环境是一个必不可少的步骤。
> "您应该根据最小特权的概念向所有域管理员用户授予其域权限。 例如，如果管理员使用特权帐户登录，并无意中运行了病毒程序，则该病毒具有对本地计算机和整个域的管理访问权限。 如果管理员改为使用非特权登录， (非管理性的) 帐户，病毒的损坏范围将只是本地计算机，因为它作为本地计算机用户运行。
> "在另一个示例中，你向其授予域级管理员权限的帐户不能在另一个林中具有提升权限，即使林之间存在信任关系也是如此。 如果攻击者设法泄露一个托管林，这种策略可帮助防止出现大范围损失。 组织应定期审核其网络，以防未经授权的权限提升。 "

以下摘录摘自 [Microsoft Windows 安全资源工具包](https://www.microsoftpressstore.com/store/microsoft-windows-security-resource-kit-9780735621749)，第一次发布于2005：

> "对执行任务所需的最少特权，始终考虑安全问题。 如果某个应用程序的权限过多，攻击者可能会受到攻击，但如果应用程序的权限尽可能少，则攻击者可能会将其展开。 例如，检查网络管理员无意中打开了用于启动病毒的电子邮件附件的后果。 如果管理员使用域管理员帐户登录，则该病毒将对域中的所有计算机具有管理员特权，从而无限制地访问网络上几乎所有的数据。 如果管理员使用本地管理员帐户登录，则该病毒将在本地计算机上具有管理员权限，因此可以访问计算机上的任何数据，并在计算机上安装恶意软件（如密钥-笔划日志记录软件）。 如果管理员使用普通用户帐户登录，则该病毒仅对管理员的数据具有访问权限，并且不能安装恶意软件。 使用阅读电子邮件所需的最少权限，在此示例中，可能会大大降低危害范围。 "

## <a name="the-privilege-problem"></a>权限问题

上述摘录中所述的原则并未发生变化，但在评估 Active Directory 安装时，我们总是发现过多的帐户，这些帐户的权利和权限远远超过了执行日常工作所需的权限。 环境的大小会影响过多特权帐户的原始数量，但 proportionmidsized 目录可能在最高特权组中具有几十个帐户，而大型安装可能有数百甚至数千个帐户。 有少量例外，无论攻击者的技能和集中的复杂性如何，攻击者通常都遵循最小抵抗的路径。 它们仅当更简单的机制失败或防守企图时，它们才会提高其工具和方法的复杂性。

遗憾的是，在许多环境中具有最小抵抗的路径证明，具有广泛和深层权限的帐户滥用。 广泛的权限是允许某个帐户在整个环境中跨部分执行特定活动的权限，例如，咨询台人员可能被授予允许他们重置多个用户帐户的密码的权限。

深层权限是应用于总体的一小部分的功能强大的特权，如在服务器上提供工程师管理员权限，以便他们能够执行修复。 广泛的权限和深层权限都不一定是危险的，但是当域中的许多帐户被永久授予广泛的深度权限时，如果只有一个帐户受到危害，则可以快速将环境重新配置为攻击者的目的，甚至销毁基础结构的大段。

传递哈希攻击（这是一种凭据被盗攻击的一种类型）无处不在，因为用于执行它们的工具可以自由地使用且易于使用，并且很多环境容易受到攻击。 然而，传递哈希攻击并不是真正的问题。 问题的关键是双重的：

1. 通常，攻击者很容易在一台计算机上获得深层权限，然后将该权限广泛地传播到其他计算机。
2. 在计算环境中，通常有太多的具有高级别权限的永久帐户。

即使消除了传递哈希攻击，攻击者也只需使用不同的策略，而不是其他策略。 它们可能会种植记录击键的恶意软件，或者利用任何其他方法来捕获跨环境的强大凭据，而不是使用包含凭据盗窃工具的恶意软件。 无论采用何种策略，目标都将保持不变：具有广泛和深度权限的帐户。

仅在受攻击的环境中 Active Directory，才能授予过多特权。 如果组织制定了授予比所需权限更多的权限，则通常会在整个基础结构中找到它，如以下各节所述。

## <a name="in-active-directory"></a>在 Active Directory

在 Active Directory 中，通常会发现 EA、DA 和 BA 组包含过多的帐户。 最常见的是，组织的 EA 组包含最少的成员，DA 组通常包含 EA 组中用户的倍数，并且管理员组通常包含比其他组的人口组合更多的成员。 这通常是因为，管理员在某种程度上比 DAs 或 EAs 的权限更小。 尽管授予这些组中每个组的权利和权限各不相同，但它们应该被有效地看作是一个功能强大的组，因为一个成员可以使自己或自己成为另两个组的成员。

## <a name="on-member-servers"></a>在成员服务器上

在许多环境中检索成员服务器上的本地管理员组的成员身份时，我们发现成员身份范围从几个本地和域帐户到多个嵌套组，这些组在展开后会显示数百甚至数千个具有服务器上的本地管理员权限的帐户。 在许多情况下，具有大型成员身份的域组嵌套在成员服务器的本地 Administrators 组中，无需考虑这样一种情况：可以修改域中这些组的成员身份的任何用户都可以获得对该组已嵌套在本地管理员组中的所有系统的管理控制。

## <a name="on-workstations"></a>在工作站上

尽管与成员服务器相比，工作站的本地管理员组中的成员通常要少得多，但在许多环境中，用户在其个人计算机上被授予了本地管理员组的成员身份。 发生这种情况时，即使启用了 UAC，这些用户也会向其工作站的完整性带来提升的风险。

> [!IMPORTANT]
> 你应仔细考虑用户是否需要其工作站的管理权限，如果用户这样做，更好的方法可能是在作为 Administrators 组成员的计算机上创建单独的本地帐户。 用户需要提升权限时，他们可以提供该本地帐户的凭据以进行提升，但由于该帐户是本地的，因此它不能用于破坏其他计算机或访问域资源。 但是，与任何本地帐户一样，本地特权帐户的凭据应该是唯一的;如果在多个工作站上创建具有相同凭据的本地帐户，则会公开计算机以传递哈希攻击。

## <a name="in-applications"></a>在应用程序中

在目标为组织的知识产权的攻击中，在应用程序中授予了强大权限的帐户可针对允许渗透数据。 尽管有权访问敏感数据的帐户可能被授予了域或操作系统中的提升权限，但可以操作应用程序配置或访问应用程序所带来的信息的帐户也可能会带来风险。

## <a name="in-data-repositories"></a>在数据存储库中

与其他目标相同的是，以文档和其他文件的形式尝试访问知识产权的攻击者可以将控制对文件存储区的访问权限、对文件具有直接访问权限的帐户，甚至是对文件具有访问权限的组或角色的访问权限。 例如，如果文件服务器用于存储合同文档，并且通过使用 Active Directory 组向文档授予了访问权限，则可以修改该组成员身份的攻击者可以将攻击者的帐户添加到该组并访问协定文档。 在应用程序（如 SharePoint）提供对文档的访问权限的情况下，攻击者可能会以前面所述的方式面向应用程序。

## <a name="reducing-privilege"></a>降低权限

环境越大，越复杂，管理和保护起来就越困难。 在小型组织中，检查和减少权限可能是一个相对简单的陈述，但每个其他服务器、工作站、用户帐户和在组织中使用的应用程序会添加另一个必须安全的对象。 由于可能很难甚至无法正确地保护组织的 IT 基础结构的每个方面，因此你应该首先关注其权限创建最大风险的帐户，这些帐户通常是 Active Directory 中的内置特权帐户和组，以及工作站和成员服务器上的特权本地帐户。

### <a name="securing-local-administrator-accounts-on-workstations-and-member-servers"></a>保护工作站和成员服务器上的本地管理员帐户

尽管本文档重点介绍如何保护 Active Directory （如前文所述），但对该目录的大多数攻击会作为对各个主机的攻击而开始。 不能提供用于保护成员系统上的本地组的完整指南，但是可以使用以下建议来帮助你保护工作站和成员服务器上的本地管理员帐户。

#### <a name="securing-local-administrator-accounts"></a>保护本地管理员帐户

在目前处于主流支持的所有 Windows 版本中，本地管理员帐户在默认情况下处于禁用状态，这将使该帐户无法用于传递哈希和其他凭据被盗攻击。 但是，在包含旧版操作系统或启用了本地管理员帐户的域中，可以使用这些帐户，如前文所述，在成员服务器和工作站之间传播安全漏洞。 出于此原因，建议将以下控件用于已加入域的系统上的所有本地管理员帐户。

[附录 H：保护本地管理员帐户和组](../../../ad-ds/plan/security-best-practices/Appendix-H--Securing-Local-Administrator-Accounts-and-Groups.md)中提供了有关实现这些控制的详细说明。 但是，在实现这些设置之前，请确保当前未在环境中使用本地管理员帐户在计算机上运行服务，或执行不应使用这些帐户的其他活动。 在生产环境中实施这些设置之前，请对它们进行全面测试。

#### <a name="controls-for-local-administrator-accounts"></a>本地管理员帐户的控件

内置管理员帐户永远不应用作成员服务器上的服务帐户，也不应使用它们登录到本地计算机 (除了安全模式，即使) 已禁用该帐户，也是如此。 实现此处所述设置的目标是防止每台计算机的本地管理员帐户可用，除非首先反转保护控制。 通过实现这些控制和监视管理员帐户的更改，你可以显著降低以本地管理员帐户为目标的攻击成功的可能性。

##### <a name="configuring-gpos-to-restrict-administrator-accounts-on-domain-joined-systems"></a>配置 Gpo 以限制加入域的系统上的管理员帐户

在你创建的一个或多个 Gpo 并链接到每个域中的工作站和成员服务器 Ou，将管理员帐户添加到 " **计算机配置 \windows 设置 \ 本地策略 \ 用户权限分配**" 中的以下用户权限：

- 拒绝通过网络访问该计算机
- 拒绝以批处理作业登录
- 拒绝以服务登录
- 拒绝通过远程桌面服务登录

当你将管理员帐户添加到这些用户权限时，请指定你是通过标记帐户的方式添加本地管理员帐户还是域的管理员帐户。 例如，要将 NWTRADERS 域的管理员帐户添加到这些拒绝权限，请将该帐户键入为 **NWTRADERS\Administrator**，或浏览到 NWTRADERS 域的管理员帐户。 若要确保限制本地管理员帐户，请在组策略对象编辑器中的这些用户权限设置中键入 " **管理员** "。

> [!NOTE]
> 即使已重命名本地管理员帐户，策略仍将适用。

这些设置将确保计算机的管理员帐户不能用于连接到其他计算机，即使它被意外或恶意启用也是如此。 无法完全禁用使用本地管理员帐户的本地登录，也不应尝试执行此操作，因为计算机的本地管理员帐户设计为在灾难恢复方案中使用。

如果成员服务器或工作站没有被授予管理权限的其他本地帐户，则该计算机可以在安全模式下启动，可以启用管理员帐户，然后可以使用该帐户在计算机上进行修复。 完成修复后，应再次禁用管理员帐户。

### <a name="securing-local-privileged-accounts-and-groups-in-active-directory"></a>在 Active Directory 中保护本地特权帐户和组

*定律6：计算机的安全性只是管理员可信任的。* - [安全性 (的十个永恒定律) 版本2.0 ](https://www.microsoft.com/en-us/msrc?rtc=1)

此处提供的信息旨在提供有关在 Active Directory 中保护最高权限内置帐户和组的一般准则。 [附录 D：在 Active Directory 中保护内置管理员帐户](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)的详细分步说明，附录[E：在 Active Directory 中保护企业管理员组](../../../ad-ds/plan/security-best-practices/Appendix-E--Securing-Enterprise-Admins-Groups-in-Active-Directory.md)，[附录 F：保护 Active Directory 中的域管理员组](../../../ad-ds/plan/security-best-practices/Appendix-F--Securing-Domain-Admins-Groups-in-Active-Directory.md)，[附录 G：保护 Active Directory 中的管理员组](../../../ad-ds/plan/security-best-practices/Appendix-G--Securing-Administrators-Groups-in-Active-Directory.md)。

在实现这些设置中的任何一种之前，还应测试所有设置，以确定它们是否适合您的环境。 并非所有组织都能实现这些设置。

#### <a name="securing-built-in-administrator-accounts-in-active-directory"></a>保护 Active Directory 中的内置管理员帐户

在 Active Directory 的每个域中，将在创建域的过程中创建管理员帐户。 默认情况下，此帐户是域中 Domain Admins 和 Administrator 组的成员，并且如果域是目录林根级域，则该帐户也是 Enterprise Admins 组的成员。 只应为初始构建活动和灾难恢复方案保留域的本地管理员帐户的使用。 若要确保在不能使用其他帐户的情况下，可以使用内置的管理员帐户来影响修复，则不应在林中的任何域中更改管理员帐户的默认成员身份。 相反，你应该遵循指导原则来帮助保护林中每个域中的管理员帐户。 [附录 D：在 Active Directory 中保护内置管理员帐户](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)中提供了有关实现这些控制的详细说明。

#### <a name="controls-for-built-in-administrator-accounts"></a>内置管理员帐户的控件

实现此处所述的设置的目标是防止每个域的管理员帐户 (不能使用组) ，除非反转了许多控件。 通过实现这些控制和监视管理员帐户的更改，你可以通过利用域的管理员帐户大大降低成功攻击的可能性。 对于林中每个域中的管理员帐户，应配置下列设置。

##### <a name="enable-the-account-is-sensitive-and-cannot-be-delegated-flag-on-the-account"></a>启用帐户上的 "敏感帐户，不能被委派" 标志

默认情况下，Active Directory 中的所有帐户都可以被委派。 委托允许计算机或服务向其他计算机提供对计算机或服务的身份验证的凭据，以代表该帐户获取服务。 如果在基于域的帐户上启用该 **帐户是敏感帐户，不能被委派** 属性，则不能向网络上的其他计算机或服务提供该帐户的凭据，这会限制利用委派来使用其他系统上的帐户凭据的攻击。

##### <a name="enable-the-smart-card-is-required-for-interactive-logon-flag-on-the-account"></a>启用帐户上的 "交互式登录需要智能卡" 标志

如果在帐户上启用 " **交互式登录" 属性需要智能卡** ，Windows 会将该帐户的密码重置为120个字符的随机值。 通过在内置管理员帐户上设置此标志，可以确保该帐户的密码不仅长而复杂，而且对任何用户都是未知的。 在启用此属性之前，不需要为帐户创建智能卡，但如有可能，应在配置帐户限制之前为每个管理员帐户创建智能卡，并将智能卡存储在安全的位置。

尽管 **交互式登录标志需要设置智能卡** ，但它不会阻止有权重置帐户密码的用户将帐户设置为已知值，并使用帐户的名称和新密码来访问网络上的资源。 因此，应在帐户上实现以下附加控件。

##### <a name="configuring-gpos-to-restrict-domains-administrator-accounts-on-domain-joined-systems"></a>在已加入域的系统上配置 Gpo 以限制域的管理员帐户

尽管禁用域中的管理员帐户会使帐户有效地变得不可用，但应在帐户被无意或恶意启用时对该帐户实施附加限制。 尽管这些控件最终可以由管理员帐户反转，但目标是创建控制来降低攻击者的进度，并限制帐户的损害。

在你创建的一个或多个 Gpo 中，并链接到每个域中的工作站和成员服务器 Ou，将每个域的管理员帐户添加到 " **计算机配置 \windows 设置 \ 本地策略 \ 用户权限分配**" 中的以下用户权限：

- 拒绝通过网络访问该计算机
- 拒绝以批处理作业登录
- 拒绝以服务登录
- 拒绝通过远程桌面服务登录

> [!NOTE]
> 向此设置添加本地管理员帐户时，必须指定是要配置本地管理员帐户还是域管理员帐户。 例如，要将 NWTRADERS 域的本地管理员帐户添加到这些拒绝权限，则必须将该帐户键入为 **NWTRADERS\Administrator**，或浏览到 NWTRADERS 域的本地管理员帐户。 如果在组策略对象编辑器中的 "用户权限" 设置中键入 **管理员** ，将限制 GPO 应用到的每台计算机上的本地管理员帐户。
>
> 建议以与基于域的管理员帐户相同的方式限制成员服务器和工作站上的本地管理员帐户。 因此，通常应将林中每个域的管理员帐户和本地计算机的管理员帐户添加到这些用户权限设置。

##### <a name="configuring-gpos-to-restrict-administrator-accounts-on-domain-controllers"></a>配置 Gpo 以限制域控制器上的管理员帐户

在林中的每个域中，应修改默认域控制器策略或链接到域控制器 OU 的策略，以将每个域的管理员帐户添加到 " **计算机配置 \windows 设置 \ 安全设置 \ 本地策略 \ 用户权限分配**" 中的以下用户权限：

- 拒绝通过网络访问该计算机
- 拒绝以批处理作业登录
- 拒绝以服务登录
- 拒绝通过远程桌面服务登录

> [!NOTE]
> 这些设置将确保本地管理员帐户无法用于连接到域控制器，但如果启用该帐户，该帐户可以本地登录到域控制器。 因为此帐户只应在灾难恢复方案中启用并使用，所以预计将至少有一个域控制器的物理访问可用，或者可以使用具有远程访问域控制器权限的其他帐户。

##### <a name="configure-auditing-of-built-in-administrator-accounts"></a>配置内置管理员帐户的审核

在保护每个域的管理员帐户并将其禁用后，应将审核配置为监视对帐户的更改。 如果该帐户已启用、其密码被重置或对该帐户进行了任何其他修改，则应将警报发送到负责管理 AD DS 的用户或团队，以及组织中的事件响应团队。

### <a name="securing-administrators-domain-admins-and-enterprise-admins-groups"></a>保护 Administrators、Domain Admins 和 Enterprise Admins 组

#### <a name="securing-enterprise-admin-groups"></a>保护企业管理员组

位于林根域中的 Enterprise Admins 组在日常工作中不应包含任何用户，前提是域的本地管理员帐户可能例外，前提是该帐户是安全的（如前文所述），并且在 [附录 D：在 Active Directory 中保护内置管理员帐户](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)。

需要 EA 访问时，其帐户需要 EA 权限和权限的用户应暂时置于 Enterprise Admins 组中。 尽管用户使用的是具有高特权的帐户，但他们的活动应该经过审核，并且最好是在执行更改的用户的情况下执行，另一位用户会观察更改，从而最大程度地减少意外滥用或配置错误。 完成活动后，应从 EA 组中删除帐户。 这可以通过手动过程和记录的进程、第三方特权标识/访问管理 (PIM/PAM) 软件或二者的组合来实现。 [附录 I：在 Active Directory 中为受保护的帐户和组创建管理帐户](../../../ad-ds/manage/component-updates/Appendix-I--Creating-Management-Accounts-for-Protected-Accounts-and-Groups-in-Active-Directory.md)中提供了用于[Attractive Accounts for Credential Theft](../../../ad-ds/plan/security-best-practices/Attractive-Accounts-for-Credential-Theft.md)在 Active Directory 中提供用于控制特权组成员身份的帐户的准则。

默认情况下，企业管理员是林中每个域内内置 Administrators 组的成员。 从每个域中的管理员组中删除 Enterprise Admins 组是不适当的修改，因为在林灾难恢复方案中，可能需要 EA 权限。 如果已从林中的管理员组中删除 Enterprise Admins 组，则应将其添加到每个域中的 Administrators 组，并应实施以下附加控件：

- 如前文所述，Enterprise Admins 组不应在日常工作中包含任何用户，这可能是目录林根级域的管理员帐户的例外，应按照 [附录 D：保护内置管理员帐户的 Active Directory 中](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)所述进行保护。
- 在链接到包含每个域中成员服务器和工作站的 Ou 的 Gpo 中，EA 组应添加到以下用户权限：
   - 拒绝通过网络访问该计算机
   - 拒绝以批处理作业登录
   - 拒绝以服务登录
   - 拒绝本地登录
   - 拒绝通过远程桌面服务登录。

这会阻止 EA 组的成员登录到成员服务器和工作站。 如果使用跳转服务器来管理域控制器和 Active Directory，请确保 "跳转服务器" 位于已限制的 Gpo 未链接到的 OU 中。

- 审核应配置为在对 EA 组的属性或成员身份进行任何修改时发送警报。 这些警报至少应发送给负责 Active Directory 管理和事件响应的用户或团队。 还应定义临时填充 EA 组的过程和过程，包括执行组的合法填充时的通知过程。

#### <a name="securing-domain-admins-groups"></a>保护域管理员组

与 Enterprise Admins 组一样，域管理员组中的成员身份只应在生成或灾难恢复方案中是必需的。 除了域的本地管理员帐户（ [在 Active Directory 中保护内置管理员帐户](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)中所述），在 DA 组中不应有任何日常用户帐户，但该域的本地管理员帐户除外。

如果需要访问 DA，则需要此访问级别的帐户应暂时放置在相关域的 "DA" 组中。 尽管用户使用高特权帐户，但应审核活动，并且最好是在执行更改的用户的情况下执行，另一个用户会观察更改，以最大程度地降低意外滥用或配置错误的可能性。 活动完成后，应从 Domain Admins 组中删除帐户。 这可以通过手动过程和记录的过程来实现，通过第三方特权标识/访问管理 (PIM/PAM) 软件，或者两者的组合。 [附录 I：在 Active Directory 中为受保护帐户和组创建管理帐户](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Appendix-I--Creating-Management-Accounts-for-Protected-Accounts-and-Groups-in-Active-Directory.md)中提供了用于创建可用于控制 Active Directory 中特权组的成员身份的帐户的准则。

默认情况下，域管理员是所有成员服务器和工作站上的本地 Administrators 组的成员。 不应修改此默认嵌套，因为它会影响可支持性和灾难恢复选项。 如果已从成员服务器上的本地管理员组中删除了域管理员组，则应将这些组添加到域中的每个成员服务器和工作站上的管理员组中。 以下常规控件（ [附录 F：保护 Active Directory 中的域管理员组](../../../ad-ds/plan/security-best-practices/Appendix-F--Securing-Domain-Admins-Groups-in-Active-Directory.md) ）也应该实现。

对于林中每个域中的 Domain Admins 组：

1. 删除 DA 组中的所有成员，并在域的内置管理员帐户可能例外的情况下进行保护，前提是该帐户已受到 [以下附录 D：保护内置管理员帐户的 Active Directory 中](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)所述的保护。
2. 在链接到包含每个域中成员服务器和工作站的 Ou 的 Gpo 中，应将 DA 组添加到以下用户权限：
   - 拒绝通过网络访问该计算机
   - 拒绝以批处理作业登录
   - 拒绝以服务登录
   - 拒绝本地登录
   - 拒绝通过远程桌面服务登录

   这会阻止 DA 组的成员登录到成员服务器和工作站。 如果使用跳转服务器来管理域控制器和 Active Directory，请确保 "跳转服务器" 位于已限制的 Gpo 未链接到的 OU 中。

3. 如果对 DA 组的属性或成员身份进行任何修改，应将审核配置为发送警报。 这些警报至少应发送给负责 AD DS 管理和事件响应的用户或团队。 还应定义临时填充 DA 组的进程和过程，包括执行组的合法填充时的通知过程。

#### <a name="securing-administrators-groups-in-active-directory"></a>保护 Active Directory 中的 Administrators 组

就 EA 和 DA 组而言，Administrators (BA) 组中的成员资格仅在生成或灾难恢复方案中是必需的。 除了域的本地管理员帐户（ [在 Active Directory 中保护内置管理员帐户](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)中所述），管理员组中的用户帐户不应是域的本地管理员帐户。

需要管理员访问权限时，需要此级别访问权限的帐户应暂时放置在相关域的 "管理员" 组中。 尽管用户使用的是高度特权的帐户，但也应该审核活动，并且最好是在用户执行更改的情况下执行，另一个用户会观察更改，从而最大程度地减少意外滥用或配置错误的可能性。 完成活动后，应立即从 Administrators 组中删除帐户。 这可以通过手动过程和记录的过程来实现，通过第三方特权标识/访问管理 (PIM/PAM) 软件，或者两者的组合。

默认情况下，管理员默认情况下是其各自域中的大多数 AD DS 对象的所有者。 在生成和灾难恢复方案中，可能需要此组中的成员资格或取得对象所有权的权限。 此外，DAs 和 EAs 通过其在 Administrators 组中的默认成员身份来继承其权限。 不应修改 Active Directory 中特权组的默认组嵌套，并且应按照 [附录 G：保护 Active Directory 中的管理员组中](../../../ad-ds/plan/security-best-practices/Appendix-G--Securing-Administrators-Groups-in-Active-Directory.md)所述对每个域的管理员组进行保护，并在下面的一般说明中进行保护。

1. 删除 Administrators 组中的所有成员（如果域为本地管理员帐户，则可能例外），前提是该帐户已受保护，如 [附录 D：在 Active Directory 中保护内置管理员帐户](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)。
2. 域的 Administrators 组的成员不需要登录到成员服务器或工作站。 在链接到工作站和每个域中的成员服务器 Ou 的一个或多个 Gpo 中，应将管理员组添加到以下用户权限：
   - 拒绝通过网络访问该计算机
   - 拒绝作为批处理作业登录
   - 拒绝以服务登录
   - 这将阻止使用 "管理员" 组的成员登录或连接到成员服务器或工作站 (除非第一次违反了多个控制措施) ，其中的凭据可能会被缓存并因此受到威胁。 特权帐户绝不能用于登录到不太适用的系统，并强制实施这些控件来防范多种攻击。

3. 在林中每个域中的域控制器 OU 中，如果管理员组尚未具有这些) 权限，则应该向其授予 (以下用户权限，这将允许管理员组的成员执行全林性灾难恢复方案所需的功能：
   - 从网络访问此计算机
   - 允许本地登录
   - 允许通过远程桌面服务登录

4. 如果对 Administrators 组的属性或成员身份进行任何修改，应将审核配置为发送警报。 应至少向负责 AD DS 管理的团队成员发送这些警报。 还应将警报发送到安全组的成员，并且应定义过程来修改 Administrators 组的成员身份。 具体而言，这些过程应该包括一个过程，通过该过程，管理员组将被修改时，系统会通知安全团队，以便发送警报时，不会发出警报。 此外，在已完成使用管理员组并已从组中删除所使用的帐户时，过程将通知安全团队。

> [!NOTE]
> 当你对 Gpo 中的 Administrators 组实施限制时，Windows 除了域的 Administrators 组外，还会将设置应用于计算机的本地 Administrators 组的成员。 因此，在对管理员组实施限制时应谨慎。 尽管禁止对 Administrators 组成员进行的网络、批处理和服务登录都可以实现，但是，不能通过远程桌面服务限制本地登录或登录名。 阻止这些登录类型会阻止本地管理员组的成员对计算机进行合法的管理。 以下屏幕截图显示除了内置本地或域管理员组以外，还可阻止内置本地和域管理员帐户的滥用的配置设置。 请注意，" **拒绝通过远程桌面服务** 用户权限登录" 权限不包括 Administrators 组，因为在此设置中包含它也会阻止属于本地计算机的管理员组成员的帐户登录。 如果计算机上的服务被配置为在此部分中所述的任何特权组的上下文中运行，则实现这些设置可能会导致服务和应用程序失败。 因此，与本部分中的所有建议一样，您应该针对您的环境中的适用性全面测试设置。
>
> ![最小特权管理模型](media/Implementing-Least-Privilege-Administrative-Models/SAD_3.gif)

### <a name="role-based-access-controls-rbac-for-active-directory"></a>基于角色的访问控制 (RBAC) 用于 Active Directory

一般而言，基于角色的访问控制 (RBAC) 是一种机制，用于对用户进行分组，并根据业务规则提供对资源的访问权限。 在 Active Directory 的情况下，为 AD DS 实施 RBAC 是创建角色的过程，该角色将权限委托给其中，允许角色的成员执行日常管理任务，而无需授予过多特权。 可以通过本机工具和界面设计和实现 Active Directory RBAC，方法是利用你已拥有的软件、购买第三方产品或这些方法的任意组合。 本部分不提供实现 Active Directory RBAC 的分步说明，而是讨论在 AD DS 安装中选择实现 RBAC 的方法时应考虑的因素。

#### <a name="native-approaches-to-rbac-for-active-directory"></a>RBAC Active Directory 的本机方法

在最简单的 RBAC 实现中，你可以将角色实现为 AD DS 组，并将权限委派给允许他们在角色的指定作用域内执行日常管理的组。

在某些情况下，Active Directory 中的现有安全组可用于授予对作业功能合适的权利和权限。 例如，如果你的 IT 组织中的特定员工负责管理和维护 DNS 区域和记录，则委派这些责任的方式非常简单，只是为每个 DNS 管理员创建一个帐户，然后将该帐户添加到 Active Directory 中的 DNS 管理员组。 DNS 管理员组与更高特权的组不同，在 Active Directory 中具有很少的权限，不过，此组的成员已被委派了允许他们管理 DNS 的权限，并且仍会受到破坏和滥用，这可能会导致权限提升。

在其他情况下，你可能需要创建安全组并委派 Active Directory 对象、文件系统对象和注册表对象的权限，以允许组的成员执行指定的管理任务。 例如，如果技术支持人员负责重置忘记的密码、帮助用户解决连接问题以及对应用程序设置进行故障排除，则可能需要将用户 Active Directory 对象上的委派设置与允许技术支持用户远程连接到用户的计算机的权限相结合，以查看或修改用户的配置设置。 对于你定义的每个角色，你应该确定：

1. 角色的哪些任务成员是日常执行的，哪些任务不经常执行。
2. 角色的哪些系统和应用程序成员应被授予权限。
3. 哪些用户应该获得角色成员资格。
4. 如何对角色成员身份进行管理。

在许多环境中，手动创建基于角色的访问控制以管理 Active Directory 环境可能会很难实现和维护。 如果已明确定义了管理 IT 基础结构所需的角色和责任，则可以利用其他工具来帮助你创建可管理的本机 RBAC 部署。 例如，如果 Forefront Identity Manager (在你的环境中使用了 FIM) ，你可以使用 FIM 来自动创建和填充管理角色，这可以简化正在进行的管理。 如果使用 Microsoft 终结点 Configuration Manager 并 System Center Operations Manager (SCOM) ，则可以使用特定于应用程序的角色来委派管理和监视功能，还可以在域中的系统之间强制执行一致的配置和审核。 如果已实现 (PKI) 的公钥基础结构，则可以发出并要求负责管理环境的 IT 人员使用智能卡。 通过 FIM Credential Management (FIM CM) ，你甚至可以将管理人员的角色和凭据的管理组合在一起。

在其他情况下，组织可能更愿意考虑部署提供 "现成" 功能的第三方 RBAC 软件。 适用于 Active Directory、Windows 和非 Windows 目录和操作系统的 RBAC 的商业、现成 (COTS) 解决方案由许多供应商提供。 在本机解决方案和第三方产品之间进行选择时，应考虑以下因素：

1. 预算：通过使用你已经拥有的软件和工具投资开发 RBAC，你可以减少部署解决方案所涉及的软件成本。 但是，除非你有在创建和部署本机 RBAC 解决方案的经验丰富的人员，否则你可能需要与咨询资源联系以开发解决方案。 你应仔细权衡自定义开发的解决方案的预期成本与部署 "现成" 解决方案的成本，尤其是在你的预算有限的情况下。
2. IT 环境的组合：如果你的环境主要包含 Windows 系统，或者你已在利用 Active Directory 来管理非 Windows 系统和帐户，则自定义本机解决方案可能会提供满足你的需求的最佳解决方案。 如果你的基础结构包含许多未运行 Windows 且不受 Active Directory 管理的系统，你可能需要考虑将非 Windows 系统与 Active Directory 环境分开管理的选项。
3. 解决方案中的特权模式：如果产品依赖于其服务帐户在 Active Directory 中放置在高特权组中，但不提供不需要将过多权限授予 RBAC 软件的选项，则没有真正地降低 Active Directory 攻击面，你只会更改目录中大多数特权组的组合。 除非应用程序供应商可以为服务帐户提供控制，从而最大程度地减少被泄漏和恶意使用的帐户的概率，否则你可能想要考虑其他选项。

### <a name="privileged-identity-management"></a>Privileged Identity Management

特权标识管理 (PIM) ，有时称为特权帐户管理 (PAM) 或特权凭据管理 (PCM) 是在基础结构中管理特权帐户的设计、构造和实现方法。 一般而言，PIM 提供了一些机制，通过这些机制，帐户被授予执行生成或中断修复功能所需的临时权限和权限，而不是将特权永久附加到帐户。 是否手动创建 PIM 功能，或者通过部署第三方软件来实现该功能，可以使用以下一个或多个功能：

- 凭据 "保管库"，在这种情况下，特权帐户的密码为 "已签出" 并分配了初始密码，并在活动完成时 "签入"，在这种情况下，将在帐户上再次重置密码。
- 使用特权凭据的时间限制限制
- 一次性凭据
- 工作流生成的权限，其中包括监视和报告所执行的活动，以及在活动完成或分配的时间已过期时自动删除权限
- 将硬编码的凭据（例如用户名和密码）替换为带有应用程序编程接口的脚本中的 (Api) ，这允许根据需要从保管库中检索凭据
- 自动管理服务帐户凭据

### <a name="creating-unprivileged-accounts-to-manage-privileged-accounts"></a>创建用于管理特权帐户的无特权帐户

管理特权帐户的难题之一是，默认情况下，可以管理特权帐户和受保护帐户和组的帐户是特权和受保护的帐户。 如果 Active Directory 安装中实现了相应的 RBAC 和 PIM 解决方案，则这些解决方案可能包括允许你有效地 depopulate 目录中大多数特权组的成员身份的方法，并且仅在需要时才暂时填充组。

不过，如果实现本机 RBAC 和 PIM，应考虑创建没有权限的帐户，并在需要时使用仅在 Active Directory 中填充和 depopulating 特权组的唯一功能。 [附录 I：在 Active Directory 中创建受保护帐户和组的管理帐户](../../../ad-ds/manage/component-updates/../../../ad-ds/manage/component-updates/Appendix-I--Creating-Management-Accounts-for-Protected-Accounts-and-Groups-in-Active-Directory.md) 提供了可用于创建帐户以实现此目的的分步说明。

### <a name="implementing-robust-authentication-controls"></a>实现可靠的身份验证控制

*定律6：真的有人试图猜测密码。* - [安全管理的10个永恒定律](/previous-versions/cc722488(v=technet.10))

传递哈希和其他凭据盗窃攻击不特定于 Windows 操作系统，也不是新的。 第一次传递哈希攻击是在1997中创建的。 然而，在过去，这些攻击需要自定义的工具，其成功被击中或错失，并要求攻击者具有相对较高的技能。 在过去几年里，引入了免费的、易于使用的工具，该工具以本机方式提取凭据，导致凭据被盗攻击的数量呈指数增长。 但是，凭据盗窃攻击不是指凭据被定向并泄露的唯一机制。

尽管你应该实现控制来帮助防止凭据被盗攻击，但你还应该确定你的环境中最可能成为攻击者的帐户，并为这些帐户实现可靠的身份验证控制。 如果大多数特权帐户使用的是单个因素身份验证（例如用户名和密码） (这两个都是 "你知道的内容"，这是一种身份验证因素) ，这些帐户是弱保护的。 攻击者所需的所有信息都是了解用户名以及与帐户关联的密码的知识，并且无需进行哈希传递攻击，攻击者可以通过用户身份验证任何接受单一因素凭据的系统。

尽管实现多重身份验证不会阻止传递哈希攻击，但可以将多重身份验证与受保护的系统结合起来。 以下部分中提供了有关实施受保护系统的详细信息，请参见 [实现安全管理主机](../../../ad-ds/plan/security-best-practices/Implementing-Secure-Administrative-Hosts.md)和身份验证选项。

#### <a name="general-authentication-controls"></a>常规身份验证控件

如果尚未实现多重身份验证（例如智能卡），请考虑这样做。 智能卡可以在公钥/私钥对中实现私钥的硬件强制保护，防止用户的私钥被访问或使用，除非用户向智能卡提供正确的 PIN、密码或生物识别标识符。 即使用户的 PIN 或密码被泄露计算机上的击键记录程序截获，攻击者也必须以物理方式显示该卡。

在很长的复杂密码由于用户抵抗而被证实难以实现的情况下，智能卡提供了一种机制，用户可以通过该机制实现相对简单的 Pin 或密码，而无需凭据容易受到暴力攻击或彩虹表攻击。 智能卡 Pin 不会存储在 Active Directory 或本地 SAM 数据库中，但凭据哈希可能仍存储在已使用智能卡进行身份验证的计算机上的 LSASS 保护的内存中。

#### <a name="additional-controls-for-vip-accounts"></a>VIP 帐户的其他控件

实现智能卡或其他基于证书的身份验证机制的另一个好处是能够利用身份验证机制保证来保护 VIP 用户可以访问的敏感数据。 在功能级别设置为 Windows Server 2012 或 Windows Server 2008 R2 的域中提供身份验证机制保障。 启用后，当使用基于证书的登录方法登录时，身份验证机制保证会将管理员指定的全局组成员身份添加到用户的 Kerberos 令牌。

这样，资源管理员就可以根据用户是否使用基于证书的登录方法登录以及使用的证书类型，来控制对资源（如文件、文件夹和打印机）的访问。 例如，当用户使用智能卡登录时，可以指定用户对网络上资源的访问权限，与用户使用智能卡时的访问权限不同 (也就是说，当用户通过输入用户名和密码) 登录时，可以指定不同的访问权限。 有关身份验证机制保证的详细信息，请参阅 [Windows Server 2008 R2 循序渐进指南中的 AD DS 身份验证机制保证](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd378897(v=ws.10))。

#### <a name="configuring-privileged-account-authentication"></a>配置特权帐户身份验证

在 "对所有管理帐户 Active Directory" 中，启用 " **需要智能卡进行交互式登录** " 属性，并审核对)  (的更改，该帐户的 " **帐户** " 选项卡上的任何属性 (例如，Cn、Name、SAMAccountName、userPrincipalName 和 userAccountControl) 管理用户对象。

尽管设置 " **需要智能卡以进行交互式登录** " 帐户将帐户的密码重置为120个字符的随机值并且需要智能卡进行交互式登录，但具有允许用户更改帐户密码的权限的用户仍可以覆盖该属性，然后可以使用帐户仅使用用户名和密码建立非交互式登录。

在其他情况下，具体取决于在 Active Directory 证书服务 (AD CS) 或第三方 PKI 的 Active Directory 和证书设置中的帐户配置，可将用于管理或 VIP 帐户的用户主体名称 (UPN) 

##### <a name="upn-hijacking-for-certificate-spoofing"></a>用于证书欺骗的 UPN 劫持

尽管彻底讨论了对公钥基础结构的攻击 (Pki) 不在本文档的讨论范围内，但对于公有和私有 Pki 的攻击从2008开始呈指数级增长。 公开了公开 Pki 的行为，但对组织内部 PKI 的攻击甚至更 prolific。 这种攻击利用 Active Directory 和证书，使攻击者能够以一种难于检测的方式欺骗其他帐户的凭据。

向已加入域的系统提供身份验证的证书时，将使用证书中的 "使用者" 或 "使用者备用)  (名称" 的内容将证书映射到 Active Directory 中的用户对象。 根据证书的类型及其构造方式，证书中的使用者属性通常包含用户的公用名 (CN) ，如以下屏幕截图所示。

![最小特权管理模型](media/Implementing-Least-Privilege-Administrative-Models/SAD_4.gif)

默认情况下，Active Directory 通过将帐户的名字 + "" + 姓连接起来来构造用户的 CN。 但是，Active Directory 中的用户对象的 CN 组件不是必需的，也不一定是唯一的，因此，将用户帐户移到目录中的另一个位置会将帐户的可分辨名称更改 (DN) ，这是目录中的对象的完整路径，如前面的屏幕截图的底部窗格中所示。

由于证书使用者名称不能保证为静态或唯一，因此通常使用 "使用者可选名称" 的内容来查找 Active Directory 中的用户对象。 从企业证书颁发机构颁发给用户的证书的 SAN 属性 (Active Directory 集成的 CAs) 通常包含用户的 UPN 或电子邮件地址。 由于 Upn 保证在 AD DS 林中是唯一的，因此，通过 UPN 查找用户对象通常作为身份验证的一部分执行，并且在身份验证过程中不涉及证书。

攻击者可以利用在身份验证证书的 SAN 属性中使用 Upn 来获取诈骗证书。 如果攻击者破坏了能够在用户对象上读取和写入 Upn 的帐户，则会按如下所示实现攻击：

用户对象上的 UPN 属性 (如 VIP 用户) 暂时更改为其他值。 此外，还可以更改 SAM 帐户名称属性和 CN，不过，这通常不是出于前面所述的原因所必需的。

更改目标帐户上的 UPN 属性后，已启用的过时用户帐户或最近创建的用户帐户的 UPN 属性将更改为最初分配给目标帐户的值。 过时的已启用用户帐户是指长时间未登录但尚未禁用的帐户。 由于以下原因，要 "以无视觉的方式隐藏" 的攻击者的目标是：

1. 由于帐户已启用但最近未使用，因此使用该帐户可能不会触发警报，这是启用已禁用的用户帐户的方式。
2. 使用现有帐户不需要创建新用户帐户，管理人员可能会注意到此帐户。
3. 仍处于启用状态的过时用户帐户通常是各种安全组的成员，并被授予对网络上资源的访问权限，从而简化了对现有用户群体的访问和 "混合使用"。

现在已配置了目标 UPN 的用户帐户用于请求 Active Directory 证书服务中的一个或多个证书。

为攻击者的帐户获取证书后，"新建" 帐户和目标帐户上的 Upn 将返回到其原始值。

现在，攻击者提供了一个或多个证书，用于对资源和应用程序进行身份验证，就像用户是其帐户被临时修改的 VIP 用户一样。 尽管对攻击者可将证书和 PKI 作为其目标的所有方法的全面讨论超出了本文档的范围，但提供了这种攻击机制，目的是为了说明应该如何监视特权和 VIP 帐户的更改 AD DS，尤其是对 (帐户的 " **帐户** " 选项卡上的任何属性（例如，cn、Name、SAMAccountName、UserPrincipalName 和 userAccountControl) ）的更改。 除了监视帐户之外，您还应将可以修改帐户的人员限制为一组较小的管理用户。 同样，应保护和监视管理用户的帐户，以防止未经授权的更改。
