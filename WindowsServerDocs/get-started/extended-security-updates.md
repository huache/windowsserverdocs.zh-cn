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
ms.date: 02/21/2020
ms.openlocfilehash: 19a65f2a254fe14f7cddfbda2a84e9d00f47da56
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181843"
---
# <a name="how-to-use-windows-server-2008-and-2008-r2-extended-security-updates-esu"></a>如何使用 Windows Server 2008 和 2008 R2 的扩展安全更新 (ESU)

>适用于：Windows Server 2008 和 Windows Server 2008 R2

Windows Server 2008 和 Windows Server 2008 R2 在 2020 年 1 月14 日到达其支持生命周期的尽头。 Windows Server 长期服务频道 (LTSC) 提供至少 10 年的支持 — 5 年 的主要支持，以及 5 年的外延支持。 此支持包括常规安全更新。

支持结束也意味着安全更新结束。 这种情况可能会导致安全问题或符合性问题，并使业务应用程序面临风险。 Microsoft 建议[升级到 Windows Server 的当前版本](modernize-windows-server-2008.md)以获得最高级的安全性、性能和创新。

如果尚未升级服务器，则可在过渡期内通过以下选项来保护应用和数据：

* 将现有 Windows Server 2008 和 2008 R2 工作负荷按原样迁移到 Azure 虚拟机 (VM)。
  * 这样迁移到 Azure 会自动提供额外的 3 年扩展安全更新 (ESU)。 扩展安全更新不会在 Azure VM 的成本之上增加额外费用，也无需进行更多配置。
* 在准备升级到较新的 Windows Server 版本之前，请为服务器购买扩展安全更新订阅并保持受保护状态。
  * 在支持生命周期结束后长达 3 年的时间内会提供这些更新。

三年期的扩展更新过后，我们会停止对 Windows Server 2008 和 2008 R2 的更新。 建议尽快将 Windows Server 版本更新到较新的版本。

## <a name="what-are-extended-security-updates-for-windows-server"></a>什么是 Windows Server 的扩展安全更新？

Windows Server 的扩展安全更新 (ESU) 在 2020 年 1 月 14 日之后最多 3 年的时间内包含评级为“严重”  和“重要”  的安全更新和公告。 扩展安全更新不包括以下部分：

* 新功能
* 客户请求的非安全修补程序
* 设计更改请求

有关详细信息，请参阅[扩展安全更新常见问题解答](https://www.microsoft.com/cloud-platform/extended-security-updates)。

## <a name="how-to-use-extended-security-updates"></a>如何使用扩展安全更新

如果在 Azure 中运行 Windows Server 2008 或 2008 R2 VM，系统会自动为其启用扩展安全更新。 无需配置任何内容，且将扩展安全更新用于 Azure VM 没有额外费用。 如果将 Azure VM 配置为接收扩展安全更新，则这些更新会自动传送到 Azure VM。

对于其他环境（如本地 VM 或物理服务器），需要手动请求和配置扩展安全更新。 可以通过批量许可计划（如企业协议 (EA)、企业协议订阅 (EAS)、教育解决方案合约 (EES) 或服务器和云合约 (SCE)）购买扩展安全更新。

购买扩展安全更新后，可以使用以下方法之一来获取密钥：

* 若要从 Azure 门户获取扩展安全更新密钥，可以[在 Azure 门户中注册扩展安全更新](#register-for-extended-security-updates-on-azure-portal)。
* 也可[登录到 Microsoft 批量许可服务中心](#sign-in-to-the-microsoft-volume-licensing-service-center)以获取密钥，无需使用 Azure 门户。

### <a name="register-for-extended-security-updates-on-azure-portal"></a>在 Azure 门户中注册扩展安全更新

若要在非 Azure VM 上使用扩展安全更新，请创建一个多次激活密钥 (MAK)，并将其应用于 Windows Server 2008 和 2008 R2 计算机。 此 MAK 密钥使 Windows 更新服务器知道你可以继续接收安全更新。 请通过 Azure 门户注册扩展安全更新并管理这些密钥，即使只使用本地计算机。

> [!NOTE]
> 如果在 Azure VM 上运行 Windows Server 2008 和 2008 R2，则无需注册扩展安全更新。 对于其他环境（如本地 VM 或物理服务器），请先[购买扩展安全更新](https://www.microsoft.com/licensing/how-to-buy/how-to-buy)，然后再尝试注册和使用它们。

若要为扩展安全更新注册 VM 并创建密钥，请打开 Azure 门户并按以下说明操作：

1. 登录 [Azure 门户](https://portal.azure.com/)。
2. 在 Azure 门户顶部的搜索框中，搜索并选择“扩展安全更新”  。

    ![在 Azure 门户中搜索扩展安全更新](media/extended-security-updates/esu-portal-search.png)

    如果以前未使用扩展安全更新，请先选择“+ 创建”  来创建扩展安全更新资源。 否则，请从列表中选择资源。

3. 在“注册扩展服务更新”  下，选择“开始”  。

    ![开始在 Azure 门户中使用扩展安全更新](media/extended-security-updates/get-started-with-esu.png)

4. 若要创建第一个密钥，请选择“获取密钥”  。

    ![选择在 Azure 门户中创建密钥](media/extended-security-updates/get-key.png)

    需要有一个与你的帐户关联的 Azure 订阅，才能创建扩展安全更新资源和密钥。 如果没有与你的帐户关联的 Azure 订阅，请使用另一用户帐户登录，或者在 Azure 门户中创建 Azure 订阅。

    Azure 订阅还必须分配有“参与者”角色，否则安全更新无效。 若要检查角色，请在搜索框中输入“订阅”。 会出现一个表格，在订阅 ID 和名称旁显示角色。

    如果你不是参与者，则可要求订阅所有者更改你的角色。 若要找出订阅的所有者，请转到上一段落所述的角色表，选择订阅的名称。 接下来，请转到页面左侧的菜单，选择“访问控制(标识和访问管理)”   >   “角色分配”并查找表中的“所有者”部分。

5. 如果看到一个显示“注册获取多次激活密钥”的页面，则表示你需要先请求访问个人预览版，然后才能使用扩展安全更新。 如果看不到该页面，请跳到步骤 6。

   若要请求访问权限，请选择“加入个人预览版”  。 将会打开一个电子邮件窗口。 此电子邮件是向产品团队发送的访问请求。

    请在请求中包括以下信息：

    * 客户名称
    * Azure 订阅 ID
    * 协议编号（适用于 ESU）
    * ESU 服务器数目

    完成后，请发送该电子邮件。

    团队会查看你在请求电子邮件中提供的信息。 如果一切正常，团队会将你添加到批准列表。

    如果团队未批准你的请求，你会看到以下错误：

    [“Microsoft.WindowsESU”命令空间中找不到此资源类型](https://docs.microsoft.com/windows-server/get-started/extended-security-updates)

6. 在“Azure 详细信息”  下，选择 Azure 订阅、资源组和密钥的位置。

    在“注册详细信息”  下，输入以下信息：

    | 设置             | 值 |
    |---------------------|-------|
    | 项名称            | 密钥的显示名称，例如“Agreement01”  。 |
    | 协议编号    | 批量许可合同管理系统或用于企业协议计划的 MSLicense 生成的协议编号。 |
    | 计算机数 | 选择要安装扩展安全更新及此密钥的计算机的数量。 |
    | 操作系统    | 选择要与此密钥配合使用的操作系统，如 Windows Server 2008 或 Windows Server 2008 R2。 |

    就绪后，选择“审核 + 注册”  。

    >[!NOTE]
    >请确保已在全局筛选器中选择你加入个人预览版时使用的 Azure 订阅。 在 Azure 门户功能区中选择“筛选器”  按钮，以检查全局订阅筛选器。
    >
    > ![选择了“筛选器”按钮的 Azure 门户功能区的图像](media/azure-ribbon-filter.png)

7. 验证成功后，将显示你为新注册表资源所做的选择的摘要。 如果需要，请更正任何验证错误或更新配置选择。 Azure [使用条款](https://azure.microsoft.com/support/legal/)和[隐私策略](https://privacy.microsoft.com/privacystatement)可供查看。

    选中下面所示的复选框以确认你具有符合条件的计算机，并且密钥仅在你的组织中使用：

    ![确认密钥将仅供你的组织使用](media/extended-security-updates/confirm-key-usage.png)

    就绪后，选择“创建”  来生成 MAK。

扩展安全更新注册现在可用于你的计算机。 应将所创建的密钥应用到你希望保持符合安全更新条件的 Windows Server 2008 和 2008 R2 计算机。

### <a name="sign-in-to-the-microsoft-volume-licensing-service-center"></a>登录到 Microsoft 批量许可服务中心

如果无权访问 Azure 门户，则可使用批量许可服务中心来查看和下载激活密钥。

若要从批量许可服务中心获取密钥，请执行以下操作：

1. 转到[“批量许可服务中心”页](https://www.microsoft.com/vlsc)，使用 Azure 凭据登录。

2. 选择“许可证”   >   “关系摘要” >   “许可 ID” >   “产品密钥”。

若要详细了解如何获取符合条件的 Windows 设备的扩展安全更新，请查看[我们的技术社区帖子](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/obtaining-extended-security-updates-for-eligible-windows-devices/ba-p/1167091#)。

## <a name="download-and-apply-extended-security-updates"></a>下载和应用扩展安全更新

交付、下载和应用 Windows Server 的扩展安全更新与现有部署过程没有什么不同。 通过扩展安全更新提供的更新仅用于提高“安全性”  ，并且在每个周二修补程序日发布一次。

可以使用已适用的任何工具和过程来安装更新。 唯一的区别在于，必须使用上一节中生成的密钥来注册系统，才能下载和安装更新。

对于 Azure VM，为计算机启用扩展安全更新的过程会自动完成。 更新将进行下载和安装，而无需进行其他配置。
