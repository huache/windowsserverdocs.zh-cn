---
ms.assetid: ab97948a-c434-48f2-8313-c1a7a518e5f7
title: 创建独立联合服务器
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 112688974c7512923f14578d1617f38266229f43
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86966009"
---
# <a name="create-a-stand-alone-federation-server"></a>创建独立联合服务器

安装联合身份验证服务角色服务并在计算机上配置所需的证书后，你就可以将计算机配置为联合服务器了。 你可以使用以下过程将计算机设置为独立的 \- 联合服务器。 创建独立联合服务器的操作 \- 也会创建新的联合身份验证服务。 你确实要使用 AD FS 联合服务器配置向导创建联合服务器。  
  
> [!NOTE]  
> 对于联合 Web 单一 \- 登录 \- \( SSO \) 设计，帐户伙伴组织和资源伙伴组织中必须至少有一台联合服务器。 有关详细信息，请参阅[放置联合服务器的位置](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807127(v=ws.11))。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477) \( http： \/ \/ go.microsoft.com \/ fwlink \/ ？LinkId \= 83477 \) 。   
  
### <a name="to-create-a-stand-alone-federation-server"></a>创建独立 \- 联合服务器  
  
1.  可通过两种方法启动 AD FS 联合服务器配置向导。 若要启动该向导，请执行下列操作之一：  
  
    -   联合身份验证服务角色服务安装完成后，打开 "AD FS 管理" 管理单元 \- ，然后单击 "**概述**" 页上或 "**操作**" 窗格中的 " **AD FS 联合服务器配置向导**" 链接。  
  
    -   安装向导完成后，请打开 Windows 资源管理器，导航到**C： \\ windows \\ ADFS**文件夹，然后双击 \- **FsConfigWizard.exe**。  
  
2.  在“欢迎使用”**** 页上，验证是否已选中“创建新的联合身份验证服务”****，然后单击“下一步”****。  
  
3.  在 "**选择独立 \- 部署或场部署**" 页上，单击 "**独立 \- 联合服务器**"，然后单击 "**下一步**"。  
  
    > [!IMPORTANT]  
    > 当你 \- 在 AD FS 联合服务器配置向导 "中选择" 独立联合服务器 "选项时，与此联合身份验证服务关联的服务帐户将自动分配给 NETWORK service 帐户。 仅建议在测试实验室环境中评估 AD FS 的情况下使用 NETWORK SERVICE 作为服务帐户。 如果你打算使用 "独立 \- 联合服务器" 选项在生产环境中部署联合服务器，则必须将此服务帐户更改为更合适的服务帐户，该帐户可专用于为此新联合身份验证服务提供请求。 将服务帐户更改为除 NETWORK SERVICE 以外的其他帐户将会缓解可能会导致联合服务器易受到恶意攻击的攻击媒介。  
  
4.  在“指定联合身份验证服务名称”**** 页上，验证“SSL 证书”**** 是否显示正确。 如果没有，请从 " **SSL 证书**" 列表中选择相应的证书。  
  
    此证书是从默认网站安全套接字层 \( SSL \) 设置生成的。 如果默认网站只具有一个配置的 SSL 证书，则显示该证书并自动选择它以供使用。 如果为默认网站配置了多个 SSL 证书，此处将列出所有这些证书，并且你必须从中进行选择。 如果没有配置默认网站的 SSL 设置，则从本地计算机上的个人证书存储中的可用证书生成列表。  
  
    > [!NOTE]  
    > 如果为 IIS 配置了 SSL 证书，则该向导将不允许覆盖证书。 这可确保之前计划对 SSL 证书所做的任何 IIS 配置将得以保留。 若要解决此限制，可以删除证书或使用 IIS 管理控制台手动对其重新进行配置。  
  
5.  如果选择的 AD FS 数据库已存在，则会显示 **“检测到现有的 AD FS 配置数据库”** 页。 如果显示了该页，请单击 **“删除数据库”**，然后单击 **“下一步”**。  
  
    > [!CAUTION]  
    > 仅当你确定此 AD FS 数据库中的数据不重要，或者不在生产联合服务器场中使用时，才应选择此选项。  
  
6.  在“已准备好应用设置”**** 页上，查看详细信息。 如果设置看上去没有问题，请单击 **“下一步”**，以开始使用这些设置配置 AD FS。  
  
7.  在“配置结果”**** 页上，查看结果。 完成所有配置步骤后，单击 "**关闭**" 退出向导。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  
