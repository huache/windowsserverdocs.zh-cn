---
title: 部署文件夹重定向和脱机文件
description: 如何使用 Windows Server 将文件夹重定向和脱机文件部署到 Windows 客户端计算机。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 06/06/2019
ms.localizationpriority: medium
ms.openlocfilehash: 6d8f6bf0df67b76028945403352bd135e6641a5a
ms.sourcegitcommit: ab3967d71dcbb962079af194875de58e7c32c4e2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2020
ms.locfileid: "76967417"
---
# <a name="deploy-folder-redirection-with-offline-files"></a>部署文件夹重定向和脱机文件

>适用于：Windows 10、Windows 7、Windows 8、Windows 8.1、Windows Vista、Windows Server 2019、Windows Server 2016、Windows Server 2012、Windows Server 2012 R2、Windows Server 2008 R2、Windows Server（半年频道）

本主题介绍了如何使用 Windows Server 将文件夹重定向和脱机文件部署到 Windows 客户端计算机。

有关本主题最近更改的列表，请参阅[更改历史记录](#change-history)。

> [!IMPORTANT]
> 由于 [MS16-072](https://support.microsoft.com/help/3163622/ms16-072-security-update-for-group-policy-june-14-2016) 中所做的安全更改，我们更新了本主题的[步骤 3：为文件夹重定向创建 GPO](#step-3-create-a-gpo-for-folder-redirection)，以便 Windows 可以正确地应用文件夹重定向策略（而不是在受影响的电脑上还原重定向的文件夹）。

## <a name="prerequisites"></a>必备条件

### <a name="hardware-requirements"></a>硬件要求

文件夹重定向需要基于 x64 或 x86 的计算机；Windows® RT 不支持文件夹重定向。

### <a name="software-requirements"></a>软件要求

文件夹重定向具有以下软件要求：

- 若要管理文件夹重定向，必须以域管理员安全组、企业管理员安全组或组策略创建者所有者安全组成员身份登录。
- 客户端计算机必须运行 Windows 10、Windows 8.1、Windows 8、Windows 7、Windows Server 2019、Windows Server 2016、Windows Server（半年频道）、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2 或 Windows Server 2008。
- 客户端计算机必须加入你管理的 Active Directory 域服务 (AD DS)。
- 必须提供一台安装了组策略管理和 Active Directory 管理中心的计算机。
- 必须提供文件服务器来托管重定向的文件夹。
    - 如果文件共享使用 DFS 命名空间，则 DFS 文件夹（链接）必须具有单个目标，以防止用户在不同服务器上进行互相冲突的编辑。
    - 如果文件共享使用 DFS 复制与另一台服务器复制内容，则用户必须只能够访问源服务器，以防止用户在不同服务器上进行互相冲突的编辑。
    - 使用群集文件共享时，请在文件共享上禁用连续可用性，以避免文件夹重定向和脱机文件出现性能问题。 此外，在用户失去对连续可用文件共享访问权限后的 3 到 6 分钟内，脱机文件可能无法切换到脱机模式，这可能会让尚未使用脱机文件的“始终脱机”模式的用户感到灰心。

> [!NOTE]
> 文件夹重定向中的某些较新功能具有额外的客户端计算机和 Active Directory 架构要求。 有关详细信息，请参阅[部署主计算机](deploy-primary-computers.md)、[禁用文件夹上的脱机文件](disable-offline-files-on-folders.md)、[启用“始终脱机”模式](enable-always-offline.md)和[启用优化文件夹移动](enable-optimized-moving.md)。

## <a name="step-1-create-a-folder-redirection-security-group"></a>步骤 1：创建文件夹重定向安全组

如果环境尚未设置文件夹重定向，则第一步是创建一个安全组，其中包含希望向其应用文件夹重定向策略设置的所有用户。

下面介绍如何创建用于文件夹重定向的安全组：

1. 在装有 Active Directory 管理中心的计算机上打开服务器管理器。
2. 在“工具”菜单上，选择“Active Directory 管理中心”   。 此时将出现 Active Directory 管理中心。
3. 右键单击相应的域或 OU，选择“新建”，然后选择“组”   。
4. 在“创建组”  窗口的“组”  部分，指定以下设置：
    - 在“组名”  中，键入安全组的名称，例如：“文件夹重定向用户”  。
    - 在“组范围”中，选择“安全性”，然后选择“全局”    。
5. 在“成员”部分中选择“添加”   。 此时将出现“选择用户、联系人、计算机、服务帐户或组”对话框。
6. 键入希望向其部署文件夹重定向的用户或组的名称，选择“确定”，然后再次选择“确定”   。

## <a name="step-2-create-a-file-share-for-redirected-folders"></a>步骤 2：为重定向文件夹创建文件共享

如果还没有用于重定向文件夹的文件共享，请使用以下过程在运行 Windows Server 2012 的服务器上创建文件共享。

> [!NOTE]
> 如果在运行另一个版本的 Windows Server 的服务器上创建文件共享，则某些功能可能会有所不同或不可用。

下面介绍如何在 Windows Server 2019、Windows Server 2016 和 Windows Server 2012 上创建文件共享：

1. 在“服务器管理器”导航窗格中，选择“文件和存储服务”，然后选择“共享”以显示“共享”页   。
2. 在“共享”磁贴中，选择“任务”，然后选择“新建共享”    。 此时将出现新建共享向导。
3. 在“选择配置文件”页上，选择“SMB 共享 - 快速”   。 如果已安装文件服务器资源管理器并且要使用文件夹管理属性，则改为选择“SMB 共享 - 高级”  。
4. 在“共享位置”  页上，选择你要在其上创建共享的服务器和卷。
5. 在“共享名”页上的“共享名”框中键入共享的名称（如“Users$”）    。
    >[!TIP]
    >在创建共享时，通过在共享名后放置 ```$``` 来隐藏共享。 这会在普通浏览器中隐藏共享。
6. 在“其他设置”页上，清除“启用连续可用性”复选框（如果存在），并选择性地选中“启用基于访问的枚举”和“加密数据访问”复选框    。
7. 在“权限”页面，选择“自定义权限…”   。 将出现高级安全设置对话框。
8. 选择“禁用继承”，然后选择“将此对象上的继承权限转换为显式权限”   。
9. 请根据表 1 所述以及图 1 所示的内容来设置权限，删除未列出的组和帐户的权限，并将特殊权限添加到在步骤 1 中创建的文件夹重定向用户组。
    
    ![设置重定向文件夹共享的权限](media/deploy-folder-redirection/setting-the-permissions-for-the-redirected-folders-share.png)
    
    **图 1** 设置重定向文件夹共享的权限
10. 如果选择了“SMB 共享 – 高级”  配置文件，则在“管理属性”  页上，选择“用户文件”  文件夹使用值。
11. 如果选择了“SMB 共享 – 高级”  配置文件，则在“配额”  页上选择性地选择要应用于共享用户的配额。
12. 在“确认”页面，选择“创建”   。

### <a name="required-permissions-for-the-file-share-hosting-redirected-folders"></a>托管重定向文件夹的文件共享所需的权限

| 用户帐户  | 访问  | 适用于  |
| --------- | --------- | --------- |
| 用户帐户 | 访问 | 适用于 |
| System     | 完全控制        |    此文件夹、子文件夹和文件     |
| Administrators     | 完全控制       | 仅此文件夹        |
| 创建者/所有者     |   完全控制      |   仅子文件夹和文件      |
| 需要将数据放在共享上的用户（文件夹重定向用户）的安全组     |   列出文件夹/读取数据（高级权限）  <br /><br />创建文件夹/附加数据（高级权限）  <br /><br />读取属性（高级权限）  <br /><br />读取扩展属性（高级权限）  <br /><br />读取权限（高级权限）       |  仅此文件夹       |
| 其他组和帐户     |  无（删除）       |         |

## <a name="step-3-create-a-gpo-for-folder-redirection"></a>步骤 3:为文件夹重定向创建 GPO

如果尚未为文件夹重定向设置创建 GPO，请使用以下过程进行创建。

下面介绍如何为文件夹重定向创建 GPO：

1. 在装有组策略管理的计算机上打开服务器管理器。
2. 从“工具”菜单上，选择“组策略管理”   。
3. 右键单击要在其中安装文件夹重定向的域或 OU，然后选择“在此域中创建 GPO 并将其链接在此处”  。
4. 在“新建 GPO”对话框中，键入 GPO 的名称（如“文件夹重定向设置”），然后选择“确定”    。
5. 右键单击新创建的 GPO，然后清除“已启用链接”  复选框。 这将阻止应用该 GPO，直到已完成对它的配置为止。
6. 选中该 GPO。 在“范围”选项卡的“安全筛选”部分，选择“经过身份验证的用户”，然后选择“删除”以防止 GPO 应用于所有人     。
7. 在“安全筛选”部分中，选择“添加”   。
8. 在“选择用户、计算机或组”对话框中，键入在步骤 1 中创建的安全组的名称（如“文件夹重定向用户”），然后选择“确定”    。
9. 依次选择“委派”选项卡、“添加”，键入“经过身份验证的用户”，选择“确定”，然后再次选择“确定”以接受默认读取权限      。
    
    由于 [MS16-072](https://support.microsoft.com/help/3163622/ms16-072-security-update-for-group-policy-june-14-2016) 中所做的安全更改，因此此步骤是必需的。

> [!IMPORTANT]
> 由于 [MS16-072](https://support.microsoft.com/help/3163622/ms16-072-security-update-for-group-policy-june-14-2016) 中所做的安全更改，现在必须向经过身份验证的用户组委派文件夹重定向 GPO 的读取权限 - 否则，GPO 将不会应用于用户，如果已应用 GPO，则会删除 GPO，并将文件夹重定向回本地计算机。 有关详细信息，请参阅[部署组策略安全更新 MS16-072](https://blogs.technet.microsoft.com/askds/2016/06/22/deploying-group-policy-security-update-ms16-072-kb3163622/)。

## <a name="step-4-configure-folder-redirection-with-offline-files"></a>步骤 4：配置文件夹重定向和脱机文件

为文件夹重定向设置创建 GPO 后，编辑组策略设置以启用和配置文件夹重定向，如以下过程中所述。

> [!NOTE]
> 默认情况下，对于 Windows 客户端计算机上的重定向文件夹，脱机文件为启用状态，而对于运行 Windows Server 的计算机，脱机文件为禁用状态（除非用户进行了更改）。 若要使用组策略来控制是否启用脱机文件，请使用“允许或禁止使用脱机文件功能”策略设置  。
> 有关其他脱机文件组策略设置的信息，请参阅[启用高级脱机文件功能](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn270369(v%3dws.11)>)和[为脱机文件配置组策略](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc759721(v%3dws.10)>)。

下面介绍如何在组策略中配置文件夹重定向：

1. 在“组策略管理”中，右键单击创建的 GPO（例如“文件夹重定向设置”），然后选择“编辑”   。
2. 在“组策略管理编辑器”窗口中，依次导航到“用户配置”、“策略”、“Windows 设置”、“文件夹重定向”     。
3. 右键单击要重定向的文件夹（例如“文档”），然后选择“属性”   。
4. 在“属性”对话框中，从“设置”框中选择“基本 - 将每个人的文件夹重定向到同一位置”    。

    > [!NOTE]
    > 若要将文件夹重定向应用于运行 Windows XP 或 Windows Server 2003 的客户端计算机，请选择“设置”选项卡，然后选择“同时将重定向策略应用到 Windows 2000、Windows 2000 Server、Windows XP 和 Windows Server 2003 操作系统”复选框   。

5. 在“目标文件夹位置”部分，选择“在根路径下为每个用户创建一个文件夹”，然后在“根路径”框中，键入存储重定向文件夹的文件共享的路径，例如：\\\\fs1.corp.contoso.com\\users$    
6. 选择“设置”选项卡，然后在“策略删除”部分中，选择性地选择“删除策略后将文件夹重定向回本地用户配置文件位置”（对于管理员和用户，此设置有助于使文件夹重定向行为更具可预测性）    。
7. 选择“确定”，然后在警告对话框中选择“是”   。

## <a name="step-5-enable-the-folder-redirection-gpo"></a>步骤 5：启用文件夹重定向 GPO

完成配置文件夹重定向组策略设置后，下一步是启用 GPO，以允许将其应用于受影响的用户。

> [!TIP]
> 如果你计划实现主计算机支持或其他策略设置，现在请进行该操作，然后再启用该 GPO。 这会防止在启用主计算机支持之前将用户数据复制到非主计算机。

下面介绍了如何启用文件夹重定向 GPO：

1. 打开“组策略管理”。
2. 右键单击创建的 GPO，然后选择“已启用链接”  。 菜单项旁边会出现一个复选框。

## <a name="step-6-test-folder-redirection"></a>步骤 6：测试文件夹重定向

若要测试文件夹重定向，请使用为文件夹重定向配置的用户帐户登录到计算机。 然后确认已重定向文件夹和配置文件。

下面介绍了如何测试文件夹重定向：

1. 使用为文件夹重定向启用的用户帐户登录到主计算机（如果已启用主计算机支持）。
2. 如果用户以前已登录到计算机，则打开提升的命令提示符，然后键入以下命令以确保最新的组策略设置已应用到客户端计算机：
    
    ```PowerShell
    gpupdate /force
    ```
3. 打开文件资源管理器。
4. 右键单击重定向的文件夹（例如文档库中的“我的文档”文件夹），然后选择“属性”  。
5. 选择“位置”选项卡，并确认路径显示指定的文件共享，而不是本地路径  。

## <a name="appendix-a-checklist-for-deploying-folder-redirection"></a>附录 A：用于部署文件夹重定向的清单

| 状态           | 操作 |
| ---              | ---    |
| ☐<br>☐<br>☐    | 1.准备域<br>- 将计算机加入到域<br>- 创建用户帐户 |
| ☐<br><br><br>   | 2.为文件夹重定向创建安全组<br>- 组名：<br>- 成员： |
| ☐<br><br>       | 3.为重定向文件夹创建文件共享<br>- 文件共享名： |
| ☐<br><br>       | 4.为文件夹重定向创建 GPO<br>- GPO 名称： |
| ☐<br><br>☐<br>☐<br>☐<br>☐<br>☐ | 5.配置文件夹重定向和脱机文件策略设置<br>- 重定向文件夹：<br>- 已启用 Windows 2000、Windows XP 和 Windows Server 2003 支持？<br>- 已启用脱机文件？ （在 Windows 客户端计算机上默认启用）<br>- 已启用“始终脱机”模式？<br>- 已启用后台文件同步？<br>- 已启用重定向文件夹的优化移动？ |
| ☐<br><br>☐<br><br>☐<br>☐ | 6.（可选）启用主计算机支持<br>- 基于计算机还是基于用户？<br>- 为用户指定主计算机<br>- 用户和主计算机映射的位置：<br>-（可选）为文件夹重定向启用主计算机支持<br>-（可选）为漫游用户策略文件启用主计算机支持 |
| ☐         | 7.启用文件夹重定向 GPO |
| ☐         | 8.测试文件夹重定向 |

## <a name="change-history"></a>更改历史记录

下表总结了一些对本主题进行的最重要的更改。

| 日期 | 说明 | 原因|
| --- | --- | --- |
| 2017 年 1 月 18 日 | 向[步骤 3：为文件夹重定向创建 GPO](#step-3-create-a-gpo-for-folder-redirection) 中添加了一个步骤，以将读取权限委派给经过身份验证的用户，由于组策略安全更新，现在需要进行此操作。 | 客户反馈 |

## <a name="more-information"></a>详细信息

* [文件夹重定向、脱机文件和漫游用户策略文件](folder-redirection-rup-overview.md)
* [为文件夹重定向以及漫游用户策略文件部署主计算机](deploy-primary-computers.md)
* [启用高级脱机文件功能](enable-always-offline.md)
* [Microsoft 关于复制的用户配置文件数据的支持声明](https://blogs.technet.microsoft.com/askds/2010/09/01/microsofts-support-statement-around-replicated-user-profile-data/)
* [使用 DISM 旁加载应用](<https://docs.microsoft.com/previous-versions/windows/it-pro/windows-8.1-and-8/hh852635(v=win.10)>)
* [对基于 Windows 运行时的应用的打包、部署和查询进行故障排除](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx)
