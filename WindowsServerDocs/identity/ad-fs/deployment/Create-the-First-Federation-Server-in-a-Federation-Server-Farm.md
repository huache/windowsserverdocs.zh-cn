---
ms.assetid: 5e334c4e-75a7-453c-83e8-5ab4243cc685
title: 在联合服务器场中创建第一台联合服务器
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 0fe5c3160f661357536ef3bd60762873063c8ed0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855470"
---
# <a name="create-the-first-federation-server-in-a-federation-server-farm"></a>在联合服务器场中创建第一台联合服务器

安装联合身份验证服务角色服务并在计算机上配置所需的证书后，你就可以将计算机配置为联合服务器了。 您可以使用以下过程将计算机设置为使用 AD FS 联合服务器配置向导的新联合服务器场中的第一个联合服务器。  
  
在服务器场中创建第一个联合服务器的操作还将创建一个新的联合身份验证服务，并使此计算机成为主联合服务器。 这意味着将使用 AD FS 配置数据库的读取\/写入副本来配置此计算机。 此服务器场中的所有其他联合服务器必须将主联合服务器上所做的任何更改复制到其读取\-仅限它们存储在本地 AD FS 配置数据库的副本。 有关这一复制过程的详细信息，请参阅 [AD FS 配置数据库的角色](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)。  
  
> [!NOTE]  
> 对于 \(SSO\) 设计上的联合 Web 单一\-Sign\-，在帐户伙伴组织和资源伙伴组织中必须至少有一个联合服务器。 有关详细信息，请参阅[放置联合服务器的位置](https://technet.microsoft.com/library/dd807127.aspx)。  
  
Domain Admins 中的成员身份或委派的域帐户已被授予对 Active Directory 中的程序数据容器的写访问权限，这是完成此过程所需的最低要求。  
  
### <a name="to-create-the-first-federation-server-in-a-federation-server-farm"></a>在联合服务器场中创建第一个联合服务器  
  
1.  可通过两种方法启动 AD FS 联合服务器配置向导。 若要启动该向导，可执行以下操作之一：  
  
    -   联合身份验证服务角色服务安装完成后，打开中的 AD FS 管理管理单元\-，并单击 "**概述**" 页上或 "**操作**" 窗格中的 " **AD FS 联合服务器配置向导**" 链接。  
  
    -   安装向导完成后的任意时间，打开 Windows 资源管理器，导航到**C：\\Windows\\ADFS**文件夹，然后\-双击 " **fsconfigwizard.exe**"。  
  
2.  在 **“欢迎”** 页上，确认已选择 **“创建新的联合身份验证服务”** ，然后单击 **“下一步”** 。  
  
3.  在 "**选择备用\-或场部署**" 页上，单击 "**新建联合服务器场**"，然后单击 "**下一步**"。  
  
4.  在 **“指定联合身份验证服务名称”** 页上，确认显示的 **“SSL 证书”** 正确。 如果此证书不正确，请从 **“SSL 证书”** 列表中选择适当的证书。  
  
    此证书是从默认网站安全套接字层 \(SSL\) 设置生成的。 如果只为默认网站配置了一个 SSL 证书，则会显示并自动选用该证书。 如果为默认网站配置了多个 SSL 证书，则此处将列出所有这些证书，你必须从中选择所需的证书。 如果没有为默认网站配置 SSL 设置，则会从本地计算机上的个人证书存储中提供的证书生成该列表。  
  
    > [!NOTE]  
    > 如果为 IIS 配置了 SSL 证书，则此向导不允许你覆盖证书。 这可确保为 SSL 证书保留任何所需的先前 IIS 配置。 若要解决此限制，你可以删除该证书，或者使用 IIS 管理控制台手动重新配置该证书。  
  
5.  如果选择的 AD FS 数据库已存在，则会显示 **“检测到现有的 AD FS 配置数据库”** 页。 如果显示了该页，请单击 **“删除数据库”** ，然后单击 **“下一步”** 。  
  
    > [!CAUTION]  
    > 仅当你确定此 AD FS 数据库中的数据不重要，或者不在生产联合服务器场中使用时，才应选择此选项。  
  
6.  在 **“指定服务帐户”** 页上，单击 **“浏览”** 。 在 **“浏览”** 对话框中，找到要用作此新联合服务器场中的服务帐户的域帐户，然后单击 **“确定”** 。 键入此帐户的密码，确认密码，然后单击 **“下一步”** 。  
  
    > [!NOTE]  
    > 有关指定联合服务器场的服务帐户的详细信息，请参阅[手动配置联合服务器场的服务帐户](Manually-Configure-a-Service-Account-for-a-Federation-Server-Farm.md)。 联合服务器场中的每个联合服务器都必须为要操作的场指定相同的服务帐户。 例如，如果创建的服务帐户是 contoso\\ADFS2SVC，则你为联合服务器角色配置的每台计算机以及将参与同一个场的每台计算机都必须在联合服务器配置向导中的此步骤中指定 contoso\\ADFS2SVC，以使场正常工作。  
  
7.  在 **“准备应用设置”** 页上复查详细信息。 如果设置看上去没有问题，请单击 **“下一步”** ，以开始使用这些设置配置 AD FS。  
  
8.  在 **“配置结果”** 页上复查结果。 完成所有配置步骤后，单击“关闭”  以退出向导。  
  
    > [!IMPORTANT]  
    > 出于部署的安全性，当你使用 AD FS 联合服务器配置向导配置联合服务器场时，将禁用项目解析和答复检测。 此向导将自动配置用于存储服务配置数据的 Windows 内部数据库。 但是，你可能会通过使用 "AD FS 管理" 管理\-单元中的 "**终结点**" 节点或 Windows PowerShell 中的 Enable\-enable-adfsendpoint Cmdlet 启用项目解析终结点，错误地撤消此更改。 请注意不要重新配置默认设置，以便在你同时使用联合服务器场和 Windows 内部数据库时，始终禁用此终结点。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  

