---
title: Windows 管理中心入门
description: Windows 管理中心入门
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: medium
ms.prod: windows-server
ms.date: 02/15/2019
ms.openlocfilehash: fc8e6ffa39320cfc73bf3f5bd0a5bc765ded24b4
ms.sourcegitcommit: 0a0a45bec6583162ba5e4b17979f0b5a0c179ab2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79322869"
---
# <a name="get-started-with-windows-admin-center"></a>Windows 管理中心入门

>适用于：Windows Admin Center、Windows Admin Center 预览版

> [!Tip]
> 不熟悉 Windows Admin Center？
> [了解有关 Windows Admin Center 的更多信息](../overview.md)或[立即下载](https://aka.ms/windowsadmincenter)。

## <a name="windows-admin-center-installed-on-windows-10"></a>Windows 10 上安装的 windows 管理中心

> [!IMPORTANT]
> 你必须是本地管理员组的成员才能在 Windows 10 上使用 Windows 管理中心

### <a name="selecting-a-client-certificate"></a>选择客户端证书

首次在 Windows 10 上打开 Windows 管理中心时，请确保选择*Windows 管理中心客户端*证书（否则，会收到 HTTP 403 错误，指出 "无法访问此页"）。

在 Microsoft Edge 中，当系统提示此对话框时：
 
1. 单击 "**更多选项**"

    ![](../media/launch-cert-1.png)

2. 选择标记为**Windows 管理中心客户端**的证书，然后单击 **"确定"**

    ![](../media/launch-cert-2.png)

3. 请确保选择 "**始终允许访问**"，然后单击 "**允许**"

    ![](../media/launch-cert-3.png)

## <a name="connecting-to-managed-nodes-and-clusters"></a>连接到托管节点和群集

在您完成 Windows 管理中心的安装后，您可以从主概述页添加服务器或群集进行管理。

 **添加单个服务器或群集作为托管节点**

1. 单击 "**所有连接**" 下的 " **+ 添加**"。

   ![](../media/launch/addserver0.png)

2. 选择添加服务器、群集、Windows 电脑或 Azure VM：
    
   ![](../media/launch/ChooseConnectionType.png)

3. 键入要管理的服务器或群集的名称，然后单击 "**提交**"。 服务器或群集将添加到 "概述" 页上的 "连接" 列表中。

   ![](../media/launch/addserver2.png)

   **--或--**

**大容量导入多台服务器**

 1. 在 "**添加服务器连接**" 页上，选择 "**导入服务器**" 选项卡。

    ![](../media/launch/import-servers.png)

 2. 单击 "**浏览**" 并选择一个文本文件，其中包含要添加的服务器的逗号或换行符的列表。

> [!Note]
> 通过[使用 PowerShell 导出连接](#use-powershell-to-import-or-export-your-connections-with-tags)创建的 .csv 文件包含除服务器名称之外的其他信息，与此导入方法不兼容。

  **--或--**

**通过搜索来添加服务器 Active Directory**

 1. 在 "**添加服务器连接**" 页上，选择 "**搜索 Active Directory** " 选项卡。

    ![](../media/launch/search-ad.png)

 2. 输入搜索条件，然后单击 "**搜索**"。 支持通配符（*）。

 3. 搜索完成后-选择一个或多个结果，可以选择添加标记，然后单击 "**添加**"。

## <a name="authenticate-with-the-managed-node"></a>通过托管节点进行身份验证 ##

Windows 管理中心支持通过多种机制对托管节点进行身份验证。 默认值为单一登录。

**单一登录**

您可以使用您当前的 Windows 凭据对托管节点进行身份验证。 这是默认设置，Windows 管理中心会在你添加服务器时尝试登录。 

**在部署为 Windows Server 上的服务的情况下进行的单一登录**

如果在 Windows Server 上安装了 Windows 管理中心，则需要进行其他配置才能进行单一登录。  [为委派配置环境](../configure/user-access-control.md)

**--或--**

**使用 "*管理身份*" 指定凭据**

在 "**所有连接**" 下，从列表中选择服务器，然后选择 "**管理**身份" 以指定将用于向托管节点进行身份验证的凭据：

![](../media/launch-use-6.png)

如果 Windows 管理中心正在 Windows Server 上的服务模式下运行，但未配置 Kerberos 委托，则必须重新输入您的 Windows 凭据：

![](../media/launch-use-7.png)

你可以将凭据应用于所有连接，这将为该特定浏览器会话缓存这些凭据。 如果重新加载浏览器，则必须重新输入作为凭据的**管理**。

**本地管理员密码解决方案（LAPS）**

如果你的环境使用[LAPS](https://technet.microsoft.com/mt227395.aspx)，并且在 WINDOWS 10 电脑上安装了 windows 管理中心，则可以使用 LAPS 凭据通过托管节点进行身份验证。 **如果使用此方案，请**[提供反馈](https://aka.ms/WACFeedback)。

## <a name="using-tags-to-organize-your-connections"></a>使用标记来组织连接

您可以使用标记在连接列表中标识和筛选相关服务器。  这样，你就可以在 "连接" 列表中查看服务器的子集。  如果有多个连接，此方法特别有用。

### <a name="edit-tags"></a>编辑标记

* 在 "所有连接" 列表中选择一个或多个服务器
* 在 "**所有连接**" 下，单击 "**编辑标记**"

![](../media/launch/tags-5.png)

"**编辑连接标记**" 窗格允许您从所选连接中修改、添加或删除标记：

* 若要向所选连接添加新标记，请选择 "**添加标记**"，然后输入要使用的标记名称。

* 若要使用现有标记名称标记所选连接，请选中要应用的标记名称旁的复选框。

* 若要从所有选择的连接中删除标记，请取消选中要删除的标记旁边的复选框。

* 如果将标记应用于所选连接的子集，则复选框将显示为中间状态。 您可以单击复选框将其选中，并将标记应用于所有选定的连接，或再次单击以取消选中它并从所有选定连接中删除标记。

![](../media/launch/tags-6.png)

### <a name="filter-connections-by-tag"></a>按标记筛选连接

向一个或多个服务器连接添加标记后，可以查看连接列表中的标记，并按标记筛选连接列表。

* 若要按标记进行筛选，请选择 "搜索" 框旁边的 "筛选器" 图标。
![](../media/launch/tags-7.png)
* 您可以选择 "or"、"and" 或 "not" 来修改所选标记的筛选器行为。
![](../media/launch/tags-8.png)

## <a name="use-powershell-to-import-or-export-your-connections-with-tags"></a>使用 PowerShell 通过标记导入或导出连接

[!INCLUDE [ps-connections](../includes/ps-connections.md)]

## <a name="view-powershell-scripts-used-in-windows-admin-center"></a>查看 Windows 管理中心中使用的 PowerShell 脚本

连接到服务器、群集或 PC 后，可以查看支持 Windows 管理中心中可用 UI 操作的 PowerShell 脚本。 从工具中，单击顶部应用程序栏中的 PowerShell 图标。 从下拉列表中选择一种感兴趣的命令，导航到相应的 PowerShell 脚本。

![](../media/launch/showscript.png)
