---
ms.assetid: 864ad4bc-8428-4a8b-8671-cb93b68b0c03
title: 减少 Active Directory 攻击面
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 5c151f0b152fadc4c86fc7bc0a414e9a190c0080
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88941387"
---
# <a name="reducing-the-active-directory-attack-surface"></a>减少 Active Directory 攻击面

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

本部分重点介绍用于降低 Active Directory 安装的受攻击面的技术控制。 部分包含以下信息：

- [实施最小特权管理模型](../../../ad-ds/plan/security-best-practices/../../../ad-ds/plan/security-best-practices/Implementing-Least-Privilege-Administrative-Models.md) 重点介绍如何确定使用高特权帐户进行日常管理的风险，以及提供实施建议以降低特权帐户存在的风险。

- [实现安全的管理主机](../../../ad-ds/plan/security-best-practices/Implementing-Secure-Administrative-Hosts.md) 介绍了部署专用的安全管理系统的原则，以及一些用于安全管理主机部署的示例方法。

- [保护域控制器免受攻击](../../../ad-ds/plan/security-best-practices/Securing-Domain-Controllers-Against-Attack.md) 讨论了一些策略和设置，这些策略和设置与实现安全管理主机的建议类似，其中包含一些特定于域控制器的建议，以帮助确保域控制器和用于管理它们的系统具有良好的安全性。

## <a name="privileged-accounts-and-groups-in-active-directory"></a>Active Directory 中有权限的帐户和组
本部分提供有关 Active Directory 中的特权帐户和组的背景信息，用于说明 Active Directory 中特权帐户和组之间的共性和差异。 了解这些区别后，无论你是在实现 [最小权限管理模型](../../../ad-ds/plan/security-best-practices/../../../ad-ds/plan/security-best-practices/Implementing-Least-Privilege-Administrative-Models.md) 的原义还是为你的组织自定义这些建议，你都可以使用适当的工具来确保每个组和帐户的安全。

### <a name="built-in-privileged-accounts-and-groups"></a>内置特权帐户和组
Active Directory 有助于委派管理，并在分配权限和权限时支持最低权限原则。 默认情况下，在域中具有帐户的 "常规" 用户可以读取目录中的大部分内容，但只能更改目录中非常有限的一组数据。 需要额外权限的用户可以被授予目录中内置的各种 "特权" 组的成员身份，以便他们可以执行与其角色相关的特定任务，但无法执行与职责无关的任务。 组织还可以创建专为特定作业责任定制的组，并被授予特定的权限，使 IT 员工能够执行日常管理功能，而不授予超过这些功能所需的权限。

在 Active Directory 中，三个内置组是目录中的最高特权组： Enterprise Admins、Domain Admins 和 Administrator。 以下部分介绍了每个组的默认配置和功能：

#### <a name="highest-privilege-groups-in-active-directory"></a>Active Directory 中的最高特权组

##### <a name="enterprise-admins"></a>企业管理员
Enterprise Admins (EA) 是仅存在于林根域中的组，默认情况下，它是林的所有域中的 Administrators 组的成员。 目录林根级域中的内置管理员帐户是 EA 组中唯一的默认成员。 EAs 被授予了权限，使其能够实现林范围的更改 (即，影响) 林中所有域的更改，如添加或删除域、建立林信任或提高林功能级别。 在正确设计和实现的委托模型中，仅在第一次构造林或进行特定林范围的更改（例如建立出站林信任）时才需要 EA 成员身份。 授予 EA 组的大多数权限都可以委派给较低权限的用户和组。

##### <a name="domain-admins"></a>域管理员

林中的每个域都有自己的域管理员 (DA) 组，该组是该域的 Administrators 组的成员，并且是加入到域中的每台计算机上的本地管理员组的成员。 域的 DA 组唯一的默认成员是该域的内置管理员帐户。 DAs 在其域中 "功能强大"，而 EAs 具有全林性的权限。 在正确设计和实现的委派模型中，仅在 "中断玻璃" 方案中才需要域管理员成员身份 (例如，在这种情况下，需要在域中的每台计算机上使用具有高级别权限的帐户) 。 尽管本机 Active Directory 委托机制允许委托只能在紧急情况下使用 DA 帐户，但构建有效的委派模型可能会很耗时，并且许多组织都利用第三方工具来加快过程。

##### <a name="administrators"></a>管理员
第三个组是将 DAs 和 EAs 嵌套到其中的内置域本地管理员 (BA) 组。 此组被授予了目录和域控制器上的许多直接权限和权限。 但是，域的 Administrators 组对成员服务器或工作站没有特权。 它通过计算机的本地管理员组中的成员身份授予本地特权。

> [!NOTE]
> 尽管这些是这些特权组的默认配置，但这三个组中的任何一个成员都可以操作该目录，以获取任何其他组的成员身份。 在某些情况下，获取其他组中的成员身份是非常困难的，而在其他组中则更难，但从潜在权限的角度来看，所有这三个组都应该被视为有效的等效项。

##### <a name="schema-admins"></a>Schema Admins

第四个特权组 (SA) 只存在于目录林根级域中，并且仅包含该域的内置管理员帐户作为默认成员，这类似于 Enterprise Admins 组。 架构管理员组仅适用于在需要修改 AD DS 架构) 时，临时和偶尔 (。

尽管 SA 组是可以修改 Active Directory 架构的唯一组 (即，目录的基础数据结构（如对象和属性) ），则 SA 组的权限和权限的作用域比前面介绍的组更受限制。 还经常会发现，组织制定了适当的管理 SA 组成员资格的做法，因为组中的成员身份通常不太必要，并且仅在短时间内。 这在技术上也是 Active Directory 中的 EA、DA 和 BA 组，但在很少的情况下，可以发现组织已为这些组实现类似于 SA 组的相似做法。

#### <a name="protected-accounts-and-groups-in-active-directory"></a>Active Directory 中受保护的帐户和组
在 Active Directory 中，名为 "受保护" 的帐户和组的默认权限集和组的保护方式不同于目录中的其他对象。 无论成员身份是派生自安全组还是分发组，任何受保护组中具有直接或可传递成员身份的任何帐户都 () 继承此受限的安全。


例如，如果用户是通讯组的成员，而后者又是 Active Directory 中受保护组的成员，则会将该用户对象标记为受保护的帐户。 当帐户被标记为受保护的帐户时，对象上的 adminCount 属性的值将设置为1。

> [!NOTE]
> 尽管受保护组中的可传递成员身份包括嵌套的分发和嵌套安全组，但作为嵌套通讯组成员的帐户将不会在其访问令牌中接收受保护组的 SID。 但是，可以将分发组转换为 Active Directory 中的安全组，这就是在受保护组成员枚举中包含通讯组的原因。 如果受保护的嵌套通讯组被转换为安全组，则作为以前通讯组成员的帐户将在下一次登录时接收其访问令牌中的父受保护组的 SID。

下表列出了 Active Directory 按操作系统版本和 Service Pack 级别列出的默认受保护帐户和组。

**操作系统和 Service Pack (SP) 版本中 Active Directory 的默认受保护帐户和组**

|**Windows 2000 <SP4**|**Windows 2000 SP4-Windows Server 2003**|**Windows Server 2003 SP1 +**|**Windows Server 2008-Windows Server 2012**|
|--|--|--|--|
|管理员|Account Operators|Account Operators|Account Operators|
||管理员|管理员|管理员|
||管理员|管理员|管理员|
|域管理员|备份操作员|备份操作员|备份操作员|
||Cert Publishers|||
||域管理员|域管理员|域管理员|
|企业管理员|域控制器|域控制器|域控制器|
||企业管理员|企业管理员|企业管理员|
||Krbtgt|Krbtgt|Krbtgt|
||打印操作员|打印操作员|打印操作员|
||||只读域控制器|
||复制程序|复制程序|复制程序|
|Schema Admins|Schema Admins||Schema Admins|

##### <a name="adminsdholder-and-sdprop"></a>AdminSDHolder 和 SDProp
在每个 Active Directory 域的 "系统" 容器中，会自动创建一个名为 AdminSDHolder 的对象。 AdminSDHolder 对象的目的是确保对受保护帐户和组的权限始终强制执行，而不考虑受保护的组和帐户在域中的位置。

默认情况下，每60分钟 () ，称为安全描述符传播器 (SDProp) 在持有域的 PDC 仿真器角色的域控制器上运行的过程。 SDProp 将域的 AdminSDHolder 对象上的权限与域中的受保护帐户和组的权限进行比较。 如果对任何受保护的帐户和组的权限与 AdminSDHolder 对象上的权限不匹配，则会重置受保护帐户和组的权限，使其与域的 AdminSDHolder 对象的权限相匹配。

对受保护的组和帐户禁用了权限继承，这意味着即使帐户或组移动到目录中的不同位置，它们也不会继承其新父对象的权限。 AdminSDHolder 对象上还禁用了继承，因此更改父对象的权限不会更改 AdminSDHolder 的权限。

> [!NOTE]
> 从受保护组中删除某个帐户后，该帐户将不再被视为受保护的帐户，但其 adminCount 属性将保持设置为1（如果未手动更改）。 此配置的结果是，SDProp 不再更新该对象的 Acl，但该对象仍不会从其父对象继承权限。 因此，该对象可能驻留在 (OU) 已委派权限的组织单位中，但以前受保护的对象将不会继承这些委派的权限。 可在 [Microsoft 支持部门文章 817433](https://support.microsoft.com/?id=817433)中找到用于查找和重置域中以前受保护的对象的脚本。

###### <a name="adminsdholder-ownership"></a>AdminSDHolder 所有权
Active Directory 中的大多数对象都属于域的 BA 组。 但是，默认情况下，AdminSDHolder 对象由域的 DA 组拥有。  (这种情况下，DAs 不会通过域 Administrators 组中的成员资格来派生其权限。 ) 

在早于 Windows Server 2008 的 Windows 版本中，对象的所有者可以更改对象的权限，包括授予自身最初没有的权限。 因此，域的 AdminSDHolder 对象上的默认权限会阻止作为 BA 或 EA 组成员的用户更改域的 AdminSDHolder 对象的权限。 但是，域的 Administrators 组的成员可以获得对象的所有权，并向自己授予额外的权限，这意味着此保护是基本的，只是保护对象不受域中 DA 组成员的用户的意外修改。 此外，在适用的) 组有权更改 EA) 的根域 (根域中的 AdminSDHolder 对象的属性时，BA 和 EA (。

> [!NOTE]
> DSHeuristics 的 AdminSDHolder 对象上的属性允许有限的自定义 (删除被视为受保护组并且受 AdminSDHolder 和 SDProp 影响的组) 。 如果实现此自定义项，则应认真考虑此自定义，不过，在 AdminSDHolder 中修改 dSHeuristics 的情况会很有用。 有关修改 AdminSDHolder 对象上的 dSHeuristics 属性的详细信息，请参阅 Microsoft 支持部门文章 [817433](https://support.microsoft.com/?id=817433) 和 [973840](https://support.microsoft.com/kb/973840)，以及 [附录 C： Active Directory 中的受保护帐户和组](Appendix-C--Protected-Accounts-and-Groups-in-Active-Directory.md)。

尽管此处介绍了 Active Directory 中的最特权组，但还有一些已被授予提升权限级别的其他组。 有关 Active Directory 中的所有默认和内置组以及分配给每个组的用户权限的详细信息，请参阅 [附录 B： Active Directory 中的特权帐户和组](../../../ad-ds/plan/security-best-practices/Appendix-B--Privileged-Accounts-and-Groups-in-Active-Directory.md)。
