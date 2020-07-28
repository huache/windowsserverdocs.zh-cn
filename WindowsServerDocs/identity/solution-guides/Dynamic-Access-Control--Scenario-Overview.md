---
ms.assetid: 7b22adfa-298d-413c-88d0-1231825b7d4d
title: 动态访问控制方案概述
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 4d39ee3053133286c07a93d18b5c3bd5809e3b54
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182393"
---
# <a name="dynamic-access-control-scenario-overview"></a>动态访问控制：方案概述

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

在 Windows Server 2012 中，可以在文件服务器之间应用数据监管，以控制谁可以访问信息并审核谁已访问信息。 动态访问控制可用于：

-   通过使用自动和手动文件分类来识别数据。 例如，你可以在整个组织内的文件服务器中标记数据。

-   通过应用采用中央访问策略的网络安全策略来控制对文件的访问。 例如，你可以定义有权访问组织内健康信息的用户。

-   通过对合规性报告和取证分析使用中央审核策略，审核对文件的访问。 例如，你可以确定曾访问高度敏感信息的用户。

-   通过对敏感的 Microsoft Office 文档使用自动 RMS 加密，来应用 Rights Management Services (RMS) 保护。 例如，你可以配置 RMS 对包含“健康保险流通与责任法案 (HIPAA)”信息的所有文档进行加密。

动态访问控制功能基于合作伙伴和行业应用程序可进一步利用的基础结构投资，因而它可以为使用 Active Directory 的组织提供巨大的价值。 该基础结构包括：

-   一种适用于 Windows 的全新授权和审核引擎，它可以处理条件表达式和中央策略。

-   用户声明和设备声明支持的 Kerberos 身份验证。

-   对文件分类基础结构 (FCI) 的改进。

-   RMS 扩展性支持，合作伙伴可以提供加密非 Microsoft 文件的解决方案。

## <a name="in-this-scenario"></a>本方案内容
以下方案和指南包含在内，作为此内容集的一部分：

## <a name="dynamic-access-control-content-roadmap"></a><a name="BKMK_APP"></a>动态访问控制内容指南

|方案|评估|计划|部署|操作|
|------------|------------|--------|----------|-----------|
|**方案：中心访问策略**<p>创建文件的中央访问策略允许组织集中部署和管理授权策略，包括使用用户声明、设备声明和资源属性的条件表达式。 这些策略建立在合规性与业务监管要求之上。 这些策略在 Active Directory 中创建与托管，因此使得管理和部署更为容易。<p>**跨林部署声明**<p>在 Windows Server 2012 中，AD DS 维护每个林中的 "声明字典"，并且在林中使用的所有声明类型都在 Active Directory 林级别定义。 有许多方案，其中主体可能要遍历信任边界。 此方案描述了声明如何遍历信任边界。|[动态访问控制：方案概述](Dynamic-Access-Control--Scenario-Overview.md)<p>[跨林部署声明](Deploy-Claims-Across-Forests.md)|[计划：中央访问策略部署](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f)<p>-   [将业务请求映射到中心访问策略的过程](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_1)<br />-   [动态访问控制的管理委派](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_3.1)<br />-   [规划中心访问策略的异常机制](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_3.2)<p>使用用户声明的最佳实践<p>-   [选择正确的配置以启用用户域中的声明](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_DC_OP3)<br />-   [用于启用用户声明的操作](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_3.4.2)<br />-   [在不使用中心访问策略的情况下，在文件服务器中使用用户声明的注意事项](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_5)<p>[使用设备声明和设备安全组](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_DeviceClaims)<p>-   [使用静态设备声明的注意事项](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_4.1)<br />-   [启用设备声明的操作](assetId:///0311a76d-d66c-4ddb-ade6-af586a2ad82f#BKMK_4.3)<p>部署工具<p>-   [数据分类工具包](https://go.microsoft.com/fwlink/?LinkId=%20244300)|[&#40;演示步骤部署中心访问策略&#41;](Deploy-a-Central-Access-Policy--Demonstration-Steps-.md)<p>[在演示步骤&#41;跨林部署声明 &#40;](Deploy-Claims-Across-Forests--Demonstration-Steps-.md)|-对中心访问策略建模|
|**方案：文件访问审核**<p>安全审核是用来帮助维护企业安全的功能最强大的工具之一。 安全审核的主要目标之一就是监管合规。 例如，像 Sarbanes Oxley、HIPAA 和 Payment Card Industry (PCI) 这类的行业标准要求企业遵守与数据安全和隐私权有关的一套严格的规则。 安全审核可以帮助确定此类策略是否存在；由此它们证明是否与这些标准相符。 此外，通过创建可用于取证分析的用户活动记录，安全审核可帮助发现异常的行为、识别并缓和在安全策略方面的差距并阻止不负责任的行为。|[方案：文件访问审核](Scenario--File-Access-Auditing.md)|[文件访问审核计划](Plan-for-File-Access-Auditing.md)|[利用中心审核策略部署安全审核 &#40;演示步骤&#41;](Deploy-Security-Auditing-with-Central-Audit-Policies--Demonstration-Steps-.md)|-   [监视在文件服务器上应用的中心访问策略](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574188(v=ws.11))<br />-   [监视与文件和文件夹相关的中央访问策略](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574198(v=ws.11))<br />-   [监视文件和文件夹上的资源属性](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574208(v=ws.11))<br />-   [监视声明类型](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574086(v=ws.11))<br />-   [在登录过程中监视用户和设备声明](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574082(v=ws.11))<br />-   [监视中心访问策略和规则定义](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574115(v=ws.11))<br />-   [监视资源属性定义](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574155(v=ws.11))<br />-   [监视可移动存储设备的使用情况](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574128(v=ws.11))。|
|**方案：“拒绝访问”协助**<p>现在，当用户尝试访问文件服务器上的远程文件时，能得到的仅有指示是访问被拒绝。 这将生成支持人员或 IT 管理员请求，它们需要弄清问题是什么，而管理员通常很难从用户那里得到合适的上下文，这使得解决问题更困难了。 <br />在 Windows Server 2012 中，我们的目标是尝试帮助信息工作者和业务所有者来处理访问被拒问题，并在涉及到该问题时，提供所有正确的信息以快速解决问题。 实现这一目标的挑战之一是，无法集中处理访问被拒，每个应用程序以不同的方式处理它，因此在 Windows Server 2012 中，其中一项目标是改进 Windows 资源管理器的访问被拒体验。|[方案：“拒绝访问”协助](Scenario--Access-Denied-Assistance.md)|[“拒绝访问”协助方案](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1)<p>-   [确定 "拒绝访问" 协助模型](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_1.1)<br />-   [确定谁应处理访问请求](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_12)<br />-   [自定义拒绝访问协助消息](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_13)<br />-   [规划异常](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_1.4)<br />-   [确定如何部署 "拒绝访问" 协助](assetId:///b169f0a4-8b97-4da8-ae4a-c8f1986d19e1#BKMK_1.5)|[&#40;演示步骤部署 "拒绝访问" 协助&#41;](Deploy-Access-Denied-Assistance--Demonstration-Steps-.md)||
|**方案：基于分类的 Office 文档加密**<p>敏感信息的保护主要与为组织降低风险有关。 诸如 HIPAA 或支付卡行业数据安全标准 (PCI-DSS) 等各种合规性规章制度，都规定了信息加密，而且出于商业考虑也需要加密敏感的业务信息。 但是，加密信息的成本比较高，这可能会损害企业的生产力。 因此，对于信息加密，组织往往采用不同的方法和优先级。 <br />为了支持此方案，Windows Server 2012 提供了基于其分类自动加密敏感 Windows Office 文件的功能。 这通过文件管理任务来完成，文件管理任务在文件被识别为文件服务器上的敏感文件后几秒钟，为敏感文档调用 Acitve Directory 权限管理服务器 (AD RMS) 保护。|[方案：基于分类的 Office 文档加密](Scenario--Classification-Based-Encryption-for-Office-Documents.md)|[计划部署基于分类的文档加密](assetId:///14714ba6-d6a2-45e4-aae5-d3318817e52a)|[&#40;演示步骤部署 Office 文件的加密&#41;](Deploy-Encryption-of-Office-Files--Demonstration-Steps-.md)||
|**方案：使用分类深入了解数据**<p>对数据和存储资源的依赖在大多数组织的重要性方面持续增长。 IT 管理员面对着监督更大、更复杂存储基础结构的日渐增长的挑战，而同时又担负着确保所有者总开支维持在合理水平的责任。 管理存储资源不再仅仅是涉及数据的量和可用性，还和公司政策的执行有关，和了解如何消耗存储来启用高效利用与合规减轻风险有关。 文件分类基础结构通过自动化分类流程来让你深入了解数据，以便你可以更有效地管理数据。 下列分类方法可用于文件分类基础结构：手动、编程、自动。 此方案重点介绍自动文件分类方法。|[方案：使用分类深入了解数据](Scenario--Get-Insight-into-Your-Data-by-Using-Classification.md)|[自动文件分类方案](assetId:///e3c3bb4b-3034-42b7-b391-8ef5f5851955)|[&#40;演示步骤部署自动文件分类&#41;](Deploy-Automatic-File-Classification--Demonstration-Steps-.md)||
|**方案：实现文件服务器上信息的保留**<p>保留期是文档过期前应保存的时间量。 组织不同，保留期可能也不相同。 可以将文件夹中的文件分类为具有短、中或长保留期，然后为每个保留期分配时间范围。 你可能想要通过将文件合法保留来无限期保留。 <br />文件分类基础结构和文件服务器资源管理器使用文件管理任务和文件分类，将保留期应用到一系列文件上。 可给文件夹分配一个保留期，然后使用文件管理任务配置分配的保留期的持续时间。 当文件夹中的文件将要过期时，文件所有者会收到一封通知邮件。 也可将文件分类为合法保留，这样文件管理任务就不会使文件过期。|[方案：实现文件服务器上信息的保留](Scenario--Implement-Retention-of-Information-on-File-Servers.md)|[文件服务器信息保留方案](assetId:///edf13190-7077-455a-ac01-f534064a9e0c)|[部署实现文件服务器上信息的保留 &#40;演示步骤&#41;](Deploy-Implementing-Retention-of-Information-on-File-Servers--Demonstration-Steps-.md)||

> [!NOTE]
> ReFS（弹性文件系统）不支持动态访问控制。

## <a name="see-also"></a>另请参阅

|内容类型|参考|
|----------------|--------------|
|**产品评估**|- [动态访问控制审阅者指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc732148(v=ws.10))<br>- [动态访问控制开发人员指南](https://docs.microsoft.com/previous-versions/windows/desktop/dacx/dynamic-access-control-developer-extensibility-roadmap)|
|规划|- [规划中心访问策略部署](https://docs.microsoft.com/windows-server/identity/solution-guides/scenario--central-access-policy)<br>- [规划文件访问审核](Plan-for-File-Access-Auditing.md)|
|**部署**|- [Active Directory 部署](https://docs.microsoft.com/windows-server/identity/ad-ds/deploy/ad-ds-deployment)<br>- [文件和存储服务部署](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831487(v=ws.11))|
|**操作**|[动态访问控制 PowerShell 参考](https://docs.microsoft.com/powershell/module/addsadministration/?view=win10-ps)|
|**工具和设置**|[数据分类工具包](https://www.microsoft.com/download/details.aspx?id=27123)|
|**社区资源**|[目录服务论坛](https://docs.microsoft.com/answers/topics/windows-active-directory.html)|
