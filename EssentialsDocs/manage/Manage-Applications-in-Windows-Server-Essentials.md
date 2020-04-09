---
title: 管理 Windows Server Essentials 中的应用程序
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: ae89c46a-0afd-4858-9150-ec97650f45a4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 64c740969e65da1798b5647dd01979756af8ebb9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852850"
---
# <a name="manage-applications-in-windows-server-essentials"></a>管理 Windows Server Essentials 中的应用程序

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials
 
 Windows Server Essentials 中的服务器仪表板和安装了 Windows Server Essentials Experience 角色的 Windows Server 2012 R2 使你可以执行常见的管理任务。 若要执行这些任务，请参阅以下内容：  
  
-   [仪表板中的应用程序管理任务](Manage-Applications-in-Windows-Server-Essentials.md#BKMK_1)  
  
-   [使用仪表板安装或删除外接程序](Manage-Applications-in-Windows-Server-Essentials.md#BKMK_2)  
  
##  <a name="application-management-tasks-in-the-dashboard"></a><a name="BKMK_1"></a>仪表板中的应用程序管理任务  
 仪表板的“应用程序”管理页面提供以下内容：  
  
- 已安装的加载项列表，它显示如下内容：  
  
  -   联机服务或加载项的名称  
  
  -   加载项的更新状态  
  
  -   加载项的订阅状态  
  
  -   提供加载项的公司或发布者的名称  
  
- 一个任务窗格，它包括一组用于管理选定加载项的任务  
  
- 可从 Microsoft Pinpoint 下载并安装的加载项列表  
  
  下表描述了服务器仪表板中可用的各种加载项管理任务。 某些任务特定于加载项，因此仅在你选择列表中的某个加载项时，这些任务才可见。  
  
|任务名称|说明|  
|---------------|-----------------|  
|删除加载项|将选定加载项从网络中的服务器和所有其他计算机中删除。|  
|在网络计算机上安装加载项|可帮助你计划在网络中所有其他计算机上安装选定的加载项。|  
|获取有关加载项的帮助|打开 Internet 浏览器，然后浏览到可从中搜索问题解决方案并详细了解选定加载项的网站。|  
|更新加载项|可帮助你下载并安装在服务器和网络计算机上安装的加载项的更新。|  
|续订加载项订阅|打开 Internet 浏览器，然后浏览到可从中续订加载项订阅的网站。|  
|阅读加载项的隐私声明|打开 Internet 浏览器，然后浏览到可从其中查看隐私声明的网站。|  
|如何安装或删除加载项？|打开 Internet 浏览器，然后浏览到显示“帮助”主题的网页。|  
  
##  <a name="install-or-remove-add-ins-using-the-dashboard"></a><a name="BKMK_2"></a>使用仪表板安装或删除外接程序  
 加载项是一种软件应用程序，它为服务器提供其他特性和功能。 从 Microsoft 和其他独立软件供应商 (ISV) 可获得越来越多的加载项。  
  
 在可以利用某个加载项提供的扩展功能之前，必须先在服务器上安装该加载项。  
  
#### <a name="to-install-an-add-in-from-microsoft-pinpoint"></a>从 Microsoft Pinpoint 安装加载项  
  
1.  在服务器仪表板中，单击 "**应用程序**"，然后单击 " **Microsoft 查明**" 选项卡。 出现可用外接程序列表。  
  
2.  单击要安装的加载项。 将显示该加载项的信息页。  
  
3.  在该加载项信息页上，单击“下载”，然后按照屏幕上的说明下载并安装该加载项。  
  
4.  按照向导中的说明来安装该加载项。  
  
5.  安装完成后，重新启动仪表板，打开服务器仪表板的“应用程序”页，并验证该加载项是否显示在列表视图中。  
  
#### <a name="to-install-an-add-in-from-another-provider"></a>通过其他提供程序安装加载项  
  
1.  打开 Windows 资源管理器，然后浏览到加载项安装文件的位置。  
  
2.  双击该文件以运行安装向导。  
  
3.  按照向导中的说明来安装该加载项。  
  
4.  安装完成后，重新启动仪表板，打开“应用程序”页，并验证该加载项是否显示在列表视图中。  
  
#### <a name="to-remove-an-add-in"></a>删除加载项  
  
1.  打开服务器仪表板。  
  
2.  单击“应用程序”选项卡。  
  
3.  在“加载项”选项卡上，选择要删除的加载项，然后单击“删除该加载项”。  
  
4.  在“删除加载项”窗口中单击“删除”。  
  
    > [!NOTE]
    >  可能需要重新启动仪表板以完全删除该加载项。  
  
## <a name="see-also"></a>另请参阅  
  
-   [仪表板概述](Overview-of-the-Dashboard-in-Windows-Server-Essentials.md)  
  
-   [管理 Windows Server Essentials](Manage-Windows-Server-Essentials.md)
