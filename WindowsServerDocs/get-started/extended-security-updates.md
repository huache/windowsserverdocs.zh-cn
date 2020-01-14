---
title: Windows Server 2008 和 2008 R2 的扩展安全更新
description: 了解在 Windows Server 2008 和 2008 R2 的扩展安全更新 (ESU) 的支持生命周期结束后如何使用它们。
ms.prod: windows-server
ms.technology: server-general
ms.mktglfcycl: manage
author: iainfoulds
ms.author: iainfou
ms.topic: get-started-article
ms.localizationpriority: high
ms.date: 12/16/2019
ms.openlocfilehash: a5af1ad5a730f1dc90111734a9b8b1aacc91201b
ms.sourcegitcommit: bfe9c5f7141f4f2343a4edf432856f07db1410aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/25/2019
ms.locfileid: "75466340"
---
# <a name="how-to-use-windows-server-2008-and-2008-r2-extended-security-updates-esu"></a>如何使用 Windows Server 2008 和 2008 R2 的扩展安全更新 (ESU)

>适用于：Windows Server 2008/2008 R2

Windows Server 2008 和 Windows Server 2008 R2 在 2020 年 1 月14 日到达其支持生命周期的尽头。 Windows Server 长期服务频道 (LTSC) 提供至少 10 年的支持 - 5 年 的主要支持，以及 5 年的外延支持。 此支持包括常规安全更新。

支持结束也意味着安全更新结束。 这种情况可能会导致安全问题或符合性问题，并使业务应用程序面临风险。 Microsoft 建议[升级到 Windows Server 的当前版本](modernize-windows-server-2008.md)以获得最高级的安全性、性能和创新。

如果在支持生命周期截止时间前无法升级所有服务器，那么在升级过渡期内，以下选项可帮助保护应用程序和数据：

* 将现有 Windows Server 2008 和 2008 R2 工作负荷按原样迁移到 Azure 虚拟机 (VM)。
    * 这样迁移到 Azure 会自动提供额外的 3 年扩展安全更新 (ESU)。 扩展安全更新不会在 Azure VM 的成本之上增加额外费用，也无需进行更多配置。
* 在准备升级到较新的 Windows Server 版本之前，请为服务器购买扩展安全更新订阅并保持受保护状态。
    * 在支持生命周期结束后长达 3 年的时间内会提供这些更新。

扩展更新的 3 年时间到期后，计算机将不会有任何选项可用于接收更多更新。

## <a name="what-are-extended-security-updates-for-windows-server"></a>什么是 Windows Server 的扩展安全更新？

Windows Server 的扩展安全更新 (ESU) 在 2020 年 1 月 14 日之后最多 3 年的时间内包含评级为“严重”  和“重要”  的安全更新和公告。 扩展安全更新不包括以下部分：

* 新功能
* 客户请求的非安全修补程序
* 设计更改请求

有关详细信息，请参阅[扩展安全更新常见问题解答](https://www.microsoft.com/cloud-platform/extended-security-updates)。

## <a name="register-for-extended-security-updates"></a>注册扩展安全更新

若要使用扩展安全更新，请创建一个多次激活密钥 (MAK)，并将其应用于 Windows Server 2008 和 2008 R2 计算机。 此密钥使 Windows 更新服务器知道你可以继续接收安全更新。 请使用 Azure 门户注册扩展安全更新并管理这些密钥，即使只使用本地计算机也是如此。

> [!NOTE]
> 如果在 Azure 中运行 Windows Server 2008/2008 R2 VM，则无需执行以下步骤。 Azure VM 会自动启用扩展安全更新。 不需要创建扩展安全更新资源和密钥，并且将扩展安全更新用于 Azure VM 也没有额外费用。

若要为扩展安全更新注册非 Azure VM 并创建密钥，请在 Azure 门户中完成以下步骤：

1. 登录 [Azure 门户](https://portal.azure.com/)。
1. 在 Azure 门户顶部的搜索框中，搜索并选择“扩展安全更新”  。

    ![在 Azure 门户中搜索扩展安全更新](media/extended-security-updates/esu-portal-search.png)

    如果以前未使用扩展安全更新，请先选择“+ 创建”  来创建扩展安全更新资源。 否则，请从列表中选择资源。

1. 在“注册扩展服务更新”  下，选择“开始”  。

    ![在 Azure 门户中开始使用扩展安全更新](media/extended-security-updates/get-started-with-esu.png)

1. 若要创建第一个密钥，请选择“获取密钥”  。

    ![选择在 Azure 门户中创建密钥](media/extended-security-updates/get-key.png)

    > [!NOTE]
    > 需要有一个与你的帐户关联的 Azure 订阅，才能创建扩展安全更新资源和密钥。 如果没有与你的帐户关联的 Azure 订阅，请使用不同的用户帐户登录，或者使用门户中所示的指导性步骤创建 Azure 订阅。

1. 在“Azure 详细信息”  下，选择 Azure 订阅、资源组和密钥的位置。

    在“注册详细信息”  下，输入以下信息：

    | 设置             | 值 |
    |---------------------|-------|
    | 项名称            | 密钥的显示名称，例如“Agreement01”  。 |
    | 协议编号    | 批量许可合同管理系统或用于企业协议计划的 MSLicense 生成的协议编号。 |
    | 计算机数 | 选择要安装扩展安全更新及此密钥的计算机的数量。 |
    | 操作系统    | 选择要与此密钥配合使用的操作系统，如 Windows Server 2008 或 Windows Server 2008 R2。 |

    就绪后，选择“审核 + 注册”  。

1. 验证成功后，将显示你为新注册表资源所做的选择的摘要。 如果需要，请更正任何验证错误或更新配置选择。 Azure [使用条款](https://azure.microsoft.com/support/legal/)和[隐私策略](https://privacy.microsoft.com/privacystatement)可供查看。

    选中下面所示的复选框以确认你具有符合条件的计算机，并且密钥仅在你的组织中使用：

    ![确认密钥将仅供你的组织使用](media/extended-security-updates/confirm-key-usage.png)

    就绪后，选择“创建”  来生成 MAK。

扩展安全更新注册现在可用于你的计算机。 应将所创建的密钥应用到你希望保持符合安全更新条件的 Windows Server 2008 和 2008 R2 计算机。

## <a name="download-and-apply-extended-security-updates"></a>下载和应用扩展安全更新

交付、下载和应用 Windows Server 的扩展安全更新与现有部署过程没有什么不同。 通过扩展安全更新提供的更新仅用于提高“安全性”  ，并且在每个周二修补程序日发布一次。

可以使用已适用的任何工具和过程来安装更新。 唯一的区别在于，必须使用上一节中生成的密钥来注册系统，才能下载和安装更新。

对于 Azure VM，为计算机启用扩展安全更新的过程会自动完成。 更新将进行下载和安装，而无需进行其他配置。
