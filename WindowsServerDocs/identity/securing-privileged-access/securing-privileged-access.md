---
title: 保护特权访问
description: 用于保护特权访问的分阶段方法
ms.topic: conceptual
ms.assetid: f5dec0c2-06fe-4c91-9bdc-67cc6a3ede60
ms.date: 02/25/2019
ms.author: joflore
author: MicrosoftGuyJFlo
manager: daveba
ms.reviewer: mas
ms.openlocfilehash: 5db041be6aa9a61bc248296ade4296afeaa4fb3e
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87953056"
---
# <a name="securing-privileged-access"></a>保护特权访问

>适用于：Windows Server

保护特权权访问是在现代组织中为企业资产提供安全保证的首要关键步骤。 IT 组织中的大多数或所有业务资产的安全性取决于用于管理和开发的特权帐户的完整性。 网络攻击者的目标通常是这些帐户和特权访问的其他元素，以便使用类似[哈希传递和票证传递](https://www.microsoft.com/pth)的凭据盗窃攻击来获取数据和系统的访问权限。

为保护特权访问免受顽固攻击者的攻击，必须采取一种完整且周密的方法，将这些系统与风险隔离。

## <a name="what-are-privileged-accounts"></a>什么是特权帐户？

在讨论如何保护特权帐户之前，让我们先定义特权帐户。

特权帐户（例如 Active Directory 域服务的管理员）可以直接或间接访问 IT 组织中的大多数或所有资产。一旦这些帐户被盗，就会导致严重的业务风险。

## <a name="why-securing-privileged-access-is-important"></a>为什么保护特权访问很重要？

网络攻击者的主要目的是获取 Active Directory (AD) 之类系统的特权访问权限，以便快速获取所有组织目标数据的访问权限。 传统的安全方法侧重于将网络和防火墙视作主要安全外围，但以下两种趋势大大降低了网络安全措施的有效性：

* 组织将数据和资源托管于传统网络边界之外的移动企业电脑、移动电话和平板电脑之类的设备、云服务和自带设备 (BYOD) 上
* 通过网络钓鱼和其他 Web 及电子邮件攻击，攻击者已展示了在网络边界内获取工作站访问权限的连贯且持续的能力。

这些因素要求我们在传统网络外围策略的基础上，根据身份验证和授权标识控制构建现代的安全外围。 在这里，安全外围的定义是在资产和对资产的威胁之间建立的一组一致的控制。 特权帐户可以有效地控制此新的安全外围，因此，保护特权访问权限至关重要。

![组织的标识层图示](../media/securing-privileged-access/PAW_LP_Fig2.JPG)

获得管理帐户控制权限的攻击者可以使用相应特权增强其在目标组织中的影响力，如下所示：

![获得管理帐户控制的攻击者如何使用这些权限以目标组织利益为代价追求自己的利益图示](../media/securing-privileged-access/PAW_LP_Fig3.JPG)

下图描绘了两条路径：

* 一条是“蓝色”路径，在其中使用标准用户帐户对电子邮件之类的资源进行非特权访问，并完成 Web 浏览和日常工作。

   > [!NOTE]
   > 后面介绍的蓝色路径项表示超出管理帐户范围的广泛环境保护。

* 另一条是“红色”路径，在其中对强化设备进行特权访问，降低遭受钓鱼和其他 Web 和电子邮件攻击的风险。

![路线图建立的单独管理“路径”的图示。这样管理的目的是将特权访问任务与高风险的标准用户任务（例如浏览 Web 和访问电子邮件）隔离](../media/securing-privileged-access/PAW_LP_Fig4.JPG)

## <a name="securing-privileged-access-roadmap"></a>保护特权访问路线图

路线图旨在最大程度地使用已部署的 Microsoft 技术，利用云技术来增强安全性，并集成可能已部署的任何第三方安全工具。

Microsoft 建议的路线图分为 3 个阶段：

* [第 1 阶段：头 30 天](#phase-1-quick-wins-with-minimal-operational-complexity)
   * 快速见效且具有意义深远的正面影响。
* [第 2 阶段：90 天](#phase-2-significant-incremental-improvements)
   * 显著的增量改进。
* [第 3 阶段：持续维护](#phase-3-security-improvement-and-sustainment)
   * 安全改进和支持。

路线图基于我们应对这些攻击和解决方案实施的经验，优先计划最有效和最快速的实现方案。

Microsoft 建议按照此路线图来保护特许访问权限免受顽固攻击者的攻击。 你可以对此路线图进行调整，以满足组织的现有功能和特定要求。

> [!NOTE]
> 保护特权访问需要广泛的元素，包括技术组件（主机防御、帐户保护、身份管理等）、更改流程及管理实践和知识。 路线图的时间线都是近似值，基于我们的客户实施经验制定。 具体时间因组织不同而不同，取决于环境和更改管理流程的复杂性。

## <a name="phase-1-quick-wins-with-minimal-operational-complexity"></a>第 1 阶段：快速见效且运营复杂程度很低

路线图的第 1 阶段侧重于快速解决使用频率最高的凭据盗窃和滥用攻击技术问题。 根据设计，第 1 阶段在大约 30 天内实施，详见下图：

![第 1 阶段图示：1. 单独的管理员帐户和用户帐户；2. 实时使用的本地管理员密码；3. 管理工作站第 1 阶段；4. 标识攻击检测](../media/securing-privileged-access/PAW_LP_Fig6.JPG)

### <a name="1-separate-accounts"></a>1.单独的帐户

为了将特权访问帐户与 Internet 风险（钓鱼攻击、Web 浏览）隔离，请为可以进行特权访问的所有人员创建专用帐户。 管理员不应使用特权高的帐户浏览 Web、检查电子邮件和执行日常生产力任务。 有关此方面的详细信息，可查看参考文档的[单独的管理帐户](securing-privileged-access-reference-material.md#separate-administrative-accounts)部分。

请按[在 Azure AD 中管理紧急访问帐户](/azure/active-directory/users-groups-roles/directory-emergency-access)一文中的指南操作，在本地 AD 和 Azure AD 环境中创建至少两个具有永久分配的管理员权限的紧急访问帐户。 只有在传统管理员帐户无法执行所需任务的情况下（例如遇到灾难），才应使用这些帐户。

### <a name="2-just-in-time-local-admin-passwords"></a>2.实时使用的本地管理员密码

为了降低攻击者从本地 SAM 数据库窃取本地管理员帐户密码哈希并将其滥用于攻击其他计算机的风险，组织应确保每台计算机都有唯一的本地管理员密码。 本地管理员密码解决方案 (LAPS) 工具可以在每个工作站和服务器上配置唯一的随机密码，并将其存储在受 ACL 保护的 Active Directory (AD) 中。 只有符合条件的授权用户才可以读取或请求重置这些本地管理员帐户密码。 可以从 [Microsoft 下载中心](https://aka.ms/LAPS)获得在工作站和服务器上使用的 LAPS。

[基于清洁源原则的操作标准](securing-privileged-access-reference-material.md#operational-standards-based-on-clean-source-principle)部分提供了其他指南，介绍如何通过 LAPS 和 PAW 操作某个环境。

### <a name="3-administrative-workstations"></a>3.管理工作站

对于那些具有 Azure Active Directory 管理特权和传统本地 Active Directory 管理特权的用户，初始安全措施是确保他们使用配置了[高度安全的 Windows 10 设备的标准](/windows-hardware/design/device-experiences/oem-highly-secure)的 Windows 10 设备。 特权管理员帐户不应是管理工作站的本地管理员组的成员。  需要对工作站进行配置更改时，可以利用通过用户访问控制 (UAC) 进行的特权提升。  另外，应该对工作站应用 Windows 10 安全基线，进一步强化设备。

### <a name="4-identity-attack-detection"></a>4.标识攻击检测

[Azure 高级威胁防护 (ATP)](/azure-advanced-threat-protection/what-is-atp) 是一种基于云的安全解决方案，可识别、检测并帮助调查针对本地 Active Directory 环境的高级威胁、被盗用标识和恶意内部操作。

## <a name="phase-2-significant-incremental-improvements"></a>第 2 阶段：显著的增量改进

第 2 阶段以第 1 阶段所做工作为基础，根据设计，应在大约 90 天内完成。 该阶段的步骤如此图中所示：

![第 2 阶段图示：1. Windows Hello 企业版/MFA；2. PAW 推出；3. 实时特权；4. Credential Guard；5. 泄漏的凭据；6. 横向移动漏洞检测](../media/securing-privileged-access/PAW_LP_Fig7.JPG)

### <a name="1-require-windows-hello-for-business-and-mfa"></a>1.需要 Windows Hello 企业版和 MFA

管理员可以充分利用与 Windows Hello 企业版相关联的易用性。 管理员可以在其电脑上将复杂的密码替换为强大的双重身份验证。 攻击者必须同时拥有设备和生物识别信息或 PIN，因此在员工不知情的情况下获取访问权限的难度将大幅增加。 若要更详细地了解 Windows Hello 企业版和推出路径，可阅读 [Windows Hello 企业版概述](/windows/security/identity-protection/hello-for-business/hello-overview)一文

请使用 Azure MFA 在 Azure AD 中为管理员帐户启用多重身份验证 (MFA)。 至少启用[基线保护条件访问策略](/azure/active-directory/conditional-access/baseline-protection#require-mfa-for-admins)。有关 Azure 多重身份验证的详细信息，可参阅[部署基于云的 Azure 多重身份验证](/azure/active-directory/authentication/howto-mfa-getstarted)一文

### <a name="2-deploy-paw-to-all-privileged-identity-access-account-holders"></a>2.将 PAW 部署到所有特权标识访问帐户持有者

请继续完成相关过程，将特权帐户与在电子邮件、Web 浏览和其他非管理任务中发现的威胁隔离开来，并应为所有可以对组织的信息系统进行特权访问的人员实现专用的特权访问工作站 (PAW)。 有关 PAW 部署的其他指南，可参阅[特权访问工作站](privileged-access-workstations.md#paw-phased-implementation)一文。

### <a name="3-just-in-time-privileges"></a>3.实时特权

若要缩短特权的公开时间并提高其使用情况的可视性，请使用合适的解决方案（例如下面的解决方案或其他第三方解决方案）提供实时 (JIT) 特权：

* 对于 Active Directory 域服务 (AD DS)，请使用 Microsoft 标识管理器 (MIM) 的[特权访问管理器 (PAM)](/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) 功能。
* 对于 Azure Active Directory，请使用 [Azure AD 特权标识管理 (PIM)](/azure/active-directory/privileged-identity-management/pim-deployment-plan) 功能。

### <a name="4-enable-windows-defender-credential-guard"></a>4.启用 Windows Defender Credential Guard

启用 Credential Guard 有助于保护 NTLM 密码哈希、Kerberos 票证授予票证和应用程序以域凭据形式存储的凭据。 此功能可以增加使用盗取的凭据在环境中进行透视的难度，因此可以防止凭据盗窃攻击（例如哈希传递或票证传递）。 若要了解 Credential Guard 的工作原理和部署方式，可参阅[使用 Windows Defender Credential Guard 保护派生的域凭据](/windows/security/identity-protection/credential-guard/credential-guard)一文。

### <a name="5-leaked-credentials-reporting"></a>5.报告泄漏的凭据

“为了发现层出不穷的威胁并保护客户，Microsoft 每天都要分析超过 6.5 万亿个信号”- [Microsoft By the Numbers](https://news.microsoft.com/bythenumbers/cyber-attacks)

允许 Microsoft Azure AD Identity Protection 报告凭据已泄露的用户，方便你进行补救。 组织可以利用 [Azure AD Identity Protection](/azure/active-directory/identity-protection/index) 来保护云环境和混合环境，使其免受威胁。

### <a name="6-azure-atp-lateral-movement-paths"></a>6.Azure ATP 横向移动路径

确保特权访问帐户持有者仅使用其 PAW 进行管理，这样，非特权帐户就不能通过凭据盗窃攻击（例如哈希传递和票证传递）获取特权帐户的访问权限。 [Azure ATP 横向移动路径 (LMP)](/azure-advanced-threat-protection/use-case-lateral-movement-path) 提供易于理解的报告，用于确定特权帐户可能会受攻击的情况。

## <a name="phase-3-security-improvement-and-sustainment"></a>第 3 阶段：安全改进和支持

路线图的第 3 阶段以第 1 和第 2 阶段执行的步骤为基础，目的是增强安全态势。 第 3 阶段在此图中得到直观展示：

![第 3 阶段：1. 查看 RBAC；2. 减少受攻击面；3. 将日志与 SEIM 集成；4. 泄漏的凭据的自动化](../media/securing-privileged-access/PAW_LP_Fig8.JPG)

这些功能将在之前阶段的步骤上构建，并将防御措施调整到更加主动的状态。 此阶段没有具体的时间线，实施时间可能较长，具体取决于单个组织的情况。

### <a name="1-review-role-based-access-control"></a>1.查看基于角色的访问控制

使用 [Active Directory 管理层模型](securing-privileged-access-reference-material.md)一文中概述的三层模型进行审核，确保低层级管理员不能对高层级资源（组成员身份、用户帐户上的 ACL，等等）进行管理访问。

### <a name="2-reduce-attack-surfaces"></a>2.减少受攻击面

强化标识工作负荷（包括域、域控制器、ADFS 和 Azure AD Connect），因为这些系统中的一个受损就可能会导致组织中的其他系统受损。 [减少 Active Directory 的受攻击面](../ad-ds/plan/security-best-practices/reducing-the-active-directory-attack-surface.md)和[保护标识基础结构的五个步骤](/azure/security/azure-ad-secure-steps)这两篇文章介绍了如何保护本地标识环境和混合标识环境。

### <a name="3-integrate-logs-with-siem"></a>3.将日志与 SIEM 集成

将日志记录集成到集中式 SIEM 工具可能有助于组织分析、检测和响应安全事件。 [监视 Active Directory 遭到破坏的迹象](../ad-ds/plan/security-best-practices/monitoring-active-directory-for-signs-of-compromise.md)和[附录 L：要监视的事件](../ad-ds/plan/appendix-l--events-to-monitor.md)这两篇文章介绍了应该在环境中监视的事件。

这是未来计划的部分，因为在安全信息和事件管理 (SIEM) 中聚合、创建和优化警报需要训练有素的分析师（不同于 30 天计划中的 Azure ATP，该计划包含现成的警报）

### <a name="4-leaked-credentials---force-password-reset"></a>4.凭据泄露 - 强制密码重置

继续增强安全态势，方法是：启用 Azure AD Identity Protection，在怀疑密码泄露时自动强制密码重置。 [使用风险事件触发多重身份验证和密码更改](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa)一文中的指南介绍了如何使用条件访问策略来启用此功能。

## <a name="am-i-done"></a>我是否已经完成？

简短的答案是“否”。

攻击者绝不会停止攻击，你也不应有任何松懈。 此路线图可以帮助组织防范目前已知的威胁，但是，攻击者的攻击手段会不断发展和变化。 我们的建议是，对于安全性，你应该常抓不懈，并应侧重于提高以你的环境为目标的攻击者的成本并降低其成功率。

保护特权访问不是组织安全计划的唯一部分，但却是安全策略的关键部分。
