---
title: Group Managed Service Accounts Overview
description: Windows Server 安全
ms.prod: windows-server
ms.technology: security-gmsa
ms.topic: article
ms.assetid: cef0693c-f861-48a7-a1c0-8d1bc06143ce
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 87739b503a5978173d67be90408c22339cae0df9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856970"
---
# <a name="group-managed-service-accounts-overview"></a>Group Managed Service Accounts Overview

>适用于：Windows Server（半年频道）、Windows Server 2016

适用于 IT 专业人员的本主题介绍了组托管服务帐户，具体方法是描述实用应用程序、Microsoft 实现中的更改以及硬件和软件要求。


## <a name="feature-description"></a><a name="BKMK_OVER"></a>功能描述
独立托管服务帐户（sMSA）是一种托管域帐户，可提供自动密码管理、简化的服务主体名称（SPN）管理以及将管理委派给其他管理员的能力。 此类型的托管服务帐户（MSA）是在 Windows Server 2008 R2 和 Windows 7 中引入的。

组托管服务帐户（gMSA）在域中提供同样的功能，但也会在多个服务器上扩展该功能。 连接到服务器场上托管的服务（例如网络负载平衡解决方案）时，支持相互身份验证的身份验证协议要求服务的所有实例都使用同一主体。 将 gMSA 用作服务主体时，Windows 操作系统将管理帐户密码，而不是依靠管理员管理密码。

Microsoft 密钥分发服务 \(kdssvc.dll\) 提供了安全获得最新密钥或具有 Active Directory 帐户的密钥标识符的特定密钥的机制。 密钥发行服务共享用于创建帐户密钥的机密。 这些密钥会定期更改。 对于 gMSA，域控制器会计算密钥发行服务提供的密钥的密码，以及 gMSA 的其他属性。  通过联系域控制器，成员主机可以获取当前和之前的密码值。

## <a name="practical-applications"></a><a name="BKMK_APP"></a>实用应用程序
Gmsa 为服务器场或网络负载均衡器后面的系统上运行的服务提供单个标识解决方案。 通过提供 gMSA 解决方案，可为新的 gMSA 主体配置服务，并由 Windows 处理密码管理。

使用 gMSA、服务或服务管理员不需要管理服务实例之间的密码同步。 GMSA 支持在延长时间段内保持脱机的主机，并为服务的所有实例管理成员主机。 这意味着，你可以部署支持现有客户端计算机可进行身份验证的单个身份的服务器场，而无需知道其连接到的服务的实例。

故障转移群集不支持 gMSA。 但是，如果在群集服务上运行的服务是 Windows 服务、应用池、计划任务或是本机支持的 gMSA 或 sMSA，则它们可以使用 gMSA 或 sMSA。

## <a name="software-requirements"></a><a name="BKMK_SOFT"></a>软件要求

运行用于管理 Gmsa 的 Windows PowerShell 命令需要 64\-位体系结构。

托管服务帐户依赖 Kerberos 支持的加密类型。在客户端计算机使用 Kerberos 在服务器中进行身份验证时，DC 将创建使用 DC 和服务器同时支持的加密保护的 Kerberos 服务票证。 DC 使用帐户\-的 "Msds-supportedencryptiontypes" 属性来确定服务器支持的加密，如果没有属性，则假定客户端计算机不支持更强的加密类型。 如果主机配置为不支持 RC4，则身份验证将始终失败。 出于此原因，应该始终显式针对 MSA 配置 AES。

> [!NOTE]
> 从 Windows Server 2008 R2 开始，默认情况下禁用 DES。 有关支持的加密类型的详细信息，请参阅 [Kerberos 身份验证中的变化](https://technet.microsoft.com/library/dd560670(WS.10).aspx)。

Gmsa 不适用于 Windows Server 2012 之前的 Windows 操作系统。

## <a name="server-manager-information"></a>服务器管理器信息
无需执行任何配置步骤即可使用服务器管理器或 Install\-node.js cmdlet 实现 MSA 和 gMSA。

## <a name="see-also"></a><a name="BKMK_LINKS"></a>另请参阅
下表提供了指向与托管服务帐户和组托管服务帐户相关的更多资源的链接。

|内容类型|参考|
|--------|-------|
|**产品评估**|[托管服务帐户的新增功能](what-s-new-for-managed-service-accounts.md)<p>[适用于 Windows 7 和 Windows Server 2008 R2 的托管服务帐户文档](https://technet.microsoft.com/library/ff641731(v=ws.10).aspx)<p>[服务帐户步骤\-\-步骤指南](https://technet.microsoft.com/library/dd548356(v=ws.10).aspx)|
|**规划**|尚未提供|
|**部署**|尚未提供|
|**操作**|[Active Directory 中的托管服务帐户](https://technet.microsoft.com/library/dd378925(v=ws.10).aspx)|
|**疑难解答**|尚未提供|
|**估算**|[组托管服务帐户入门](getting-started-with-group-managed-service-accounts.md)|
|**工具和设置**|[Active Directory 域服务中的托管服务帐户](https://technet.microsoft.com/library/dd378925(v=WS.10).aspx)|
|**社区资源**|[托管服务帐户：了解、实现、最佳做法和故障排除](https://blogs.technet.com/b/askds/archive/2009/09/10/managed-service-accounts-understanding-implementing-best-practices-and-troubleshooting.aspx)|
|**相关技术**|[Active Directory 域服务概述](active-directory-domain-services-overview.md)|


