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
ms.openlocfilehash: 603786d8553cce20f0b559ba8a91dfc29f760488
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855480"
---
# <a name="create-a-stand-alone-federation-server"></a>创建独立联合服务器

安装联合身份验证服务角色服务并在计算机上配置所需的证书后，你就可以将计算机配置为联合服务器了。 你可以使用以下过程将计算机设置为独立\-的联合服务器。 创建独立\-独立联合服务器的操作也会创建一个新的联合身份验证服务。 你确实要使用 AD FS 联合服务器配置向导创建联合服务器。  
  
> [!NOTE]  
> 对于 \(SSO\) 设计上的联合 Web 单一\-Sign\-，在帐户伙伴组织和资源伙伴组织中必须至少有一个联合服务器。 有关详细信息，请参阅[放置联合服务器的位置](https://technet.microsoft.com/library/dd807127.aspx)。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)\(http：\/\/go.microsoft.com\/fwlink\/？LinkId\=83477\)。   
  
### <a name="to-create-a-stand-alone-federation-server"></a>创建独立\-单机联合服务器  
  
1.  可通过两种方法启动 AD FS 联合服务器配置向导。 若要启动该向导，可执行以下操作之一：  
  
    -   联合身份验证服务角色服务安装完成后，打开中的 AD FS 管理管理单元\-，并单击 "**概述**" 页上或 "**操作**" 窗格中的 " **AD FS 联合服务器配置向导**" 链接。  
  
    -   安装向导完成后，请打开 Windows 资源管理器，导航到**C：\\Windows\\ADFS**文件夹，然后\-双击 " **fsconfigwizard.exe**"。  
  
2.  在 **“欢迎”** 页上，确认已选择 **“创建新的联合身份验证服务”** ，然后单击 **“下一步”** 。  
  
3.  在 "**选择独立\-或场部署**" 页上，单击 "**独立\-联合服务器**"，然后单击 "**下一步**"。  
  
    > [!IMPORTANT]  
    > 当你在 AD FS 联合服务器配置向导中选择 "独立\-" 联合服务器 "选项时，与此联合身份验证服务关联的服务帐户将自动分配到网络服务帐户。 仅建议在测试实验室环境中评估 AD FS 的情况下使用 NETWORK SERVICE 作为服务帐户。 如果你打算使用 "独立\-" 联合服务器 "选项在生产环境中部署联合服务器，则必须将此服务帐户更改为可专用于为此新联合身份验证服务提供服务请求的更合适服务帐户，这一点很重要。 将服务帐户更改为除 NETWORK SERVICE 以外的其他帐户将会缓解可能会导致联合服务器易受到恶意攻击的攻击媒介。  
  
4.  在 **“指定联合身份验证服务名称”** 页上，确认显示的 **“SSL 证书”** 正确。 如果没有，请从 " **SSL 证书**" 列表中选择相应的证书。  
  
    此证书是从默认网站安全套接字层 \(SSL\) 设置生成的。 如果只为默认网站配置了一个 SSL 证书，则会显示并自动选用该证书。 如果为默认网站配置了多个 SSL 证书，则此处将列出所有这些证书，你必须从中选择所需的证书。 如果没有为默认网站配置 SSL 设置，则会从本地计算机上的个人证书存储中提供的证书生成该列表。  
  
    > [!NOTE]  
    > 如果为 IIS 配置了 SSL 证书，则此向导不允许你覆盖证书。 这可确保为 SSL 证书保留任何所需的先前 IIS 配置。 若要解决此限制，可以删除证书或使用 IIS 管理控制台手动对其重新进行配置。  
  
5.  如果选择的 AD FS 数据库已存在，则会显示 **“检测到现有的 AD FS 配置数据库”** 页。 如果显示了该页，请单击 **“删除数据库”** ，然后单击 **“下一步”** 。  
  
    > [!CAUTION]  
    > 仅当你确定此 AD FS 数据库中的数据不重要，或者不在生产联合服务器场中使用时，才应选择此选项。  
  
6.  在 **“准备应用设置”** 页上复查详细信息。 如果设置看上去没有问题，请单击 **“下一步”** ，以开始使用这些设置配置 AD FS。  
  
7.  在 **“配置结果”** 页上复查结果。 完成所有配置步骤后，单击“关闭”  以退出向导。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  

