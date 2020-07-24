---
ms.assetid: 6ecf8d85-cd61-4c87-add8-00a679a6e3ff
title: 将联合服务器添加到联合服务器场
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: ae584fbf57d287a4bc1c5d21d2c27ccf3d1b5592
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86964909"
---
# <a name="add-a-federation-server-to-a-federation-server-farm"></a>将联合服务器添加到联合服务器场


安装联合身份验证服务角色服务并在计算机上配置所需的证书后，你就可以将计算机配置为联合服务器了。 可以使用以下过程将计算机加入新的联合服务器场中。  
  
使用 AD FS 联合服务器配置向导将计算机加入到场中。 使用此向导将计算机加入现有场时，将使用 AD FS 配置数据库的只读副本配置计算机， \- 并且该计算机必须从主联合服务器接收更新。  
  
> [!NOTE]  
> 对于联合 Web 单一 \- 登录 \- \( SSO \) 设计，帐户伙伴组织和资源伙伴组织中必须至少有一台联合服务器。 有关详细信息，请参阅[放置联合服务器的位置](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807127(v=ws.11))。  
  
若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477) \( http： \/ \/ go.microsoft.com \/ fwlink \/ ？LinkId \= 83477 \) 。   
  
### <a name="to-add-a-federation-server-to-a-federation-server-farm"></a>将联合服务器添加到联合服务器场  
  
1.  可通过两种方法启动 AD FS 联合服务器配置向导。 若要启动该向导，请执行下列操作之一：  
  
    -   联合身份验证服务角色服务安装完成后，打开 "AD FS 管理" 管理单元 \- ，然后单击 "**概述**" 页上或 "**操作**" 窗格中的 " **AD FS 联合服务器配置向导**" 链接。  
  
    -   安装向导完成后，请打开 Windows 资源管理器，导航到**C： \\ windows \\ ADFS**文件夹，然后双击 \- **FsConfigWizard.exe**。  
  
2.  在 **“欢迎”** 页上，确认已选择 **“将联合服务器添加到现有联合身份验证服务”**，然后单击 **“下一步”**。  
  
3.  如果您选择的 AD FS 数据库已经存在，则会出现 "**检测到现有 AD FS 配置数据库**" 页。 如果显示了该页，请单击 **“删除数据库”**，然后单击 **“下一步”**。  
  
    > [!CAUTION]  
    > 仅当你确定此 AD FS 数据库中的数据不重要，或者不在生产联合服务器场中使用时，才应选择此选项。  
  
4.  在 **“指定主联合服务器和服务帐户”** 页的 **“主联合服务器名称”** 下，键入场中主联合服务器的计算机名称，然后单击 **“浏览”**。 在 **“浏览”** 对话框中，找到现有联合服务器场中所有其他联合服务器用作服务帐户的域帐户，然后单击 **“确定”**。 键入密码并确认，然后单击 **“下一步”**：  
  
    > [!NOTE]  
    > 有关指定联合服务器场的服务帐户的详细信息，请参阅[手动配置联合服务器场的服务帐户](Manually-Configure-a-Service-Account-for-a-Federation-Server-Farm.md)。 联合服务器场中的每个联合服务器都必须为要操作的场指定相同的服务帐户。 例如，如果创建的服务帐户是 contoso \\ ADFS2SVC，则你为联合服务器角色配置的每台计算机以及将参与同一场的每台计算机都必须 \\ 在联合服务器配置向导中的此步骤中指定 contoso ADFS2SVC，以使场正常工作。  
  
5.  在“已准备好应用设置”**** 页上，查看详细信息。 如果设置看上去没有问题，请单击 **“下一步”**，以开始使用这些设置配置 AD FS。  
  
6.  在“配置结果”**** 页上，查看结果。 完成所有配置步骤后，单击 "**关闭**" 退出向导。  
  
## <a name="additional-references"></a>其他参考  
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)  
  
