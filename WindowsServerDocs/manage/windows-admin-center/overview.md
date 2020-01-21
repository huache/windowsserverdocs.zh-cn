---
title: Windows Admin Center 概述
description: 了解如何使用 Windows Admin Center (Project Honolulu) 管理 Windows Server
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 01/07/2020
ms.localizationpriority: high
ms.prod: windows-server
ms.openlocfilehash: 7b3a75258086a73fbd618c2e8221454d7e616556
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75949987"
---
# <a name="windows-admin-center"></a>Windows Admin Center

> 适用于：Windows Admin Center、Windows Admin Center 预览版

Windows Admin Center 是本地部署的基于浏览器的应用，用于管理 Windows 服务器、群集、超融合基础设施和 Windows 10 电脑。 它不会在 Windows 之外产生额外费用，并可以在生产中使用。

要查看新增功能，请参阅[版本历史记录](support/release-history.md)。

## <a name="download-now"></a>立即下载

从 Microsoft Evaluation Center 下载 [Windows Admin Center](https://www.microsoft.com/evalcenter/evaluate-windows-admin-center)  。 虽然说是“开始评估”，但这是可供生产使用的正式发布版，包含在 Windows 或 Windows Server 许可证中。

有关安装的帮助，请参阅[安装](deploy/install.md)。 有关 Windows Admin Center 入门的提示，请参阅[开始使用](use/get-started.md)。

可通过 Microsoft 更新来更新 Windows Admin Center 的非预览版，也可手动下载和安装 Windows Admin Center。 在下一个非预览版本发布之后，支持继续使用每个非预览版 Windows Admin Center 30 天。 有关详细信息，请参阅我们的[支持政策](support/index.md)。

## <a name="windows-admin-center-scenarios"></a>Windows Admin Center 场景

下面是 Windows Admin Center 的一些用途：

|     |     |
| --- | --- |
| ![](media/simple-icon.png)| **简化服务器管理** <br/> 使用服务器管理器等熟悉的工具的新式版本管理你的服务器和群集。 5 分钟内即可完成安装并立即在你的环境中管理服务器，无需目标配置。 有关详细信息，请参阅[什么是 Windows Admin Center？](understand/what-is.md)。 |
| ![](media/future-icon.png)| **与混合解决方案结合使用** <br/> 与 Azure 的集成可帮助你选择性地将本地服务器与相关云服务相连。 有关详细信息，请参阅 [Azure 混合服务](azure/index.md) |
| ![](media/secure-icon.png)| **简化超融合管理** <br/> 简化 Azure Stack HCI 或 Windows Server 超融合群集的管理。 使用简化的工作负载创建和管理 VM、存储空间直通卷和软件定义的网络等等。 有关详细信息，请参阅[能否使用 Windows Admin Center 管理超融合基础设施](use/manage-hyper-converged.md)|

下面的视频提供了概要信息，后面有张海报提供了更多详细信息：
>[!VIDEO https://www.youtube.com/embed/WCWxAp27ERk]

[![Windows Admin Center 海报](media/WAC1910Poster_thumb_small.PNG)](media/WAC1910Poster_thumb.png)

[下载 PDF](https://github.com/MicrosoftDocs/windowsserverdocs/raw/master/WindowsServerDocs/manage/windows-admin-center/media/WindowsAdminCenter1910Poster.pdf)


## <a name="contents-at-a-glance"></a>内容概览

<table>
    <tr></tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>了解</h3>
            <ul>
            <li><a href="understand/what-is.md">什么是 Windows Admin Center？</a>
            <li><a href="understand/faq.md">常见问题解答</a>
            <li><a href="understand/case-studies.md">案例研究</a>
            <li><a href="understand/related-management.md">相关管理产品</a>
            </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>计划</h3>
            <ul>
            <li><a href="plan/installation-options.md">哪种安装类型适合你？</a>
            <li><a href="plan/user-access-options.md">用户访问选项</a>
            <br>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>部署</h3>
            <ul>
            <li><a href="deploy/prepare-environment.md">准备环境</a>
            <li><a href="deploy/install.md">安装 Windows Admin Center</a>
            <li><a href="deploy/high-availability.md">实现高可用性</a>
         </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>配置</h3>
            <ul>
            <li><a href="configure/settings.md">Windows Admin Center 设置</a>
            <li><a href="configure/user-access-control.md">用户访问控制和权限</a>
            <li><a href="configure/shared-connections.md">共享连接</a>
            <li><a href="configure/using-extensions.md">扩展</a>
            <li><a href="configure/use-powershell.md">使用 Powershell 自动执行</a>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>用途</h3>
            <ul>
            <li><a href="use/get-started.md">启动和添加连接</a>
            <li><a href="use/manage-servers.md">管理服务器</a>
            <li><a href="use/deploy-hyperconverged-infrastructure.md">部署超融合基础设施</a>
            <li><a href="use/manage-hyper-converged.md">管理超融合基础设施</a>
            <li><a href="use/manage-failover-clusters.md">管理故障转移群集</a>
            <li><a href="use/manage-virtual-machines.md">管理虚拟机</a>
            <li><a href="use/logging.md">日志记录</a>
            </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>连接到 Azure</h3>
            <ul>
            <li><a href="azure/index.md">Azure 混合服务</a></li>
            <li><a href="azure/azure-integration.md">将 Windows Admin Center 连接到 Azure</a></li>
            <li><a href="azure/deploy-wac-in-azure.md">在 Azure 中部署 Windows Admin Center</a></li>
            <li><a href="azure/manage-azure-vms.md">通过 Windows Admin Center 管理 Azure 虚拟机</a></li>
            </ul>
        </td>
    </tr>
    <tr>
            <td style="vertical-align: top;">
            <h3>支持</h3>
            <ul>
            <li><a href="support/release-history.md">版本历史记录</a>
            <li><a href="support/index.md">支持策略</a>
            <li><a href="support/troubleshooting.md">常见故障排除步骤</a>
            <li><a href="support/known-issues.md">已知问题</a>
            </ul>
        </td>
            <td style="vertical-align: top;">
            <h3>Extend</h3>
            <ul>
            <li><a href="extend/extensibility-overview.md">扩展概述</a>
            <li><a href="extend/understand-extensions.md">了解扩展</a>
            <li><a href="extend/developing-extensions.md">开发扩展</a>
            <li><a href="extend/publish-extensions.md">指南</a>
            <li><a href="extend/publish-extensions.md">发布扩展</a>
            </ul>
        </td>
    </tr>

</table>

## <a name="video-based-learning"></a>基于视频的学习

下面是一些来自 Microsoft Ignite 2019 研讨会的视频：

- [Windows Admin Center：解锁 Azure 混合价值](https://aka.ms/WAC-BRK3165)
- [Windows Admin Center：新增功能和后续动向](https://aka.ms/WAC-BRK2048)
- [通过 Windows Admin Center 从 Azure 自动监视、保护和更新本地服务器](https://aka.ms/WAC-THR2146)
- [使用 Windows Admin Center 第三方扩展完成更多任务](https://aka.ms/WAC-THR2140)
- [成为 Windows Admin Center 专家：有关部署、配置和安全性的最佳做法](https://aka.ms/WAC-THR2135)
- [Windows Admin Center：与 System Center 和 Microsoft Azure 搭配使用效果更佳](https://aka.ms/WAC-THR2176)
- [如何将 Microsoft Azure 混合服务与 Windows Admin Center 和 Windows Server 一起使用](https://aka.ms/WAC-THR2073)
- [现场问答：通过 Windows Admin Center 管理混合服务器环境](https://aka.ms/WAC-MLS1055)
- [学习路径：混合管理技术](https://aka.ms/WAC-HybridMgmtTech)
- [练习实验室：Windows Admin Center 和混合](https://aka.ms/WAC-HOL2019)

下面是来自 Windows Server Summit 2019 研讨会的一些视频：

- [通过 Windows Admin Center 使用混合环境](https://aka.ms/WAC-WSS2019-GoHybridWAC)
- [Windows Admin Center v1904 的新增功能](https://aka.ms/WAC-WSS2019-WhatsNewv1904)

下面还有其他一些资源：

- [Windows Admin Center 服务器管理已重塑](https://aka.ms/WAC-ServerMgmtReimagined)
- [通过 Windows Admin Center 随处管理服务器和虚拟机](https://aka.ms/WAC-Webinar2019)
- [如何开始使用 Windows Admin Center](https://www.youtube.com/embed/PcQj6ZklmK0)

## <a name="see-how-customers-are-benefitting-from-windows-admin-center"></a>了解客户如何从 Windows Admin Center 受益

|     |
| --- |
| “[Windows Admin Center] 让我们用于管理系统的时间/工作量减少了 75% 以上。”<br> \- Rand Morimoto，Convergent Computing 总裁  |
| “感谢 [Windows Admin Center]，我们可以从 HTML5 门户正常地远程管理客户，并且与 Azure Active Directory 完全集成，感谢多重身份验证，我们能够提高安全性。”<br/> \- Silvio Di Benedetto，Inside Technologies 创始人兼高级顾问  |
| “我们已经能够以更有效的方式部署 [Server Core] SKU，进而改善了资源效率、安全性和自动化，同时仍然实现了良好的工作效率，并减少了在只依赖脚本时可能发生的错误。” <br/> \- Guglielmo Mengora，VaiSulWeb 创始人兼首席执行官  |
| “使用 [Windows Admin Center]，特别是 SMB 市场的客户现在有了易于使用的工具来管理内部基础结构。 这能够最大程度地减少管理工作量，并节省大量时间。 最重要的是：[Windows Admin Center] 没有额外的许可费用！” <br/> \- Helmut Otto，SecureGUARD 管理总监  |

[更多了解在生产环境中使用 Windows Admin Center 的公司。](understand/case-studies.md)

## <a name="related-products"></a>相关产品

Windows Admin Center 专为管理单个服务器或群集而设计。 它补充但不完全取代现有的 Microsoft 监视和管理解决方案，如远程服务器管理工具 (RSAT)、System Center、Intune 或 Azure Stack。

[了解 Windows Admin Center 如何成为其他 Microsoft 管理解决方案的补充。](understand/related-management.md)

## <a name="stay-updated"></a>保持更新

![](//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOolR)[在 Twitter 上关注我们](https://twitter.com/servermgmt)

![](//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOtyw)[阅读我们的博客](https://blogs.technet.microsoft.com/servermanagement/)
