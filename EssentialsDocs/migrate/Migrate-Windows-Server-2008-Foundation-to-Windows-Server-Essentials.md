---
title: 将 Windows Server 2008 Foundation 迁移到 Windows Server Essentials
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: f22fc0a4-cb82-4e60-afe6-2d03145745e7
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: b416e6a3ce226328bd2d65928852ce507fbc2128
ms.sourcegitcommit: fdc3ce1992f4dd6ea1771479d525126abbbcfa72
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85256617"
---
# <a name="migrate-windows-server-2008-foundation-to-windows-server-essentials"></a>将 Windows Server 2008 Foundation 迁移到 Windows Server Essentials

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本指南介绍如何将现有的 Windows Server 2008 Foundation 域迁移到 &reg; 新硬件上的 Windows server 2012 Essentials，然后迁移设置和数据。 本指南还介绍了在完成迁移后如何从 Windows Server Essentials 网络中删除现有的服务器。  
  
> [!NOTE]
>  为了避免迁移过程中出现问题，Windows Server Essentials 产品开发团队强烈建议你在开始迁移之前先阅读本文档。  
  
## <a name="additional-resources"></a>其他资源  
 有关可帮助指导你完成迁移过程的其他信息、工具和社区资源的链接，请参阅[Windows Small Business Server 迁移](https://go.microsoft.com/fwlink/?LinkId=217520)。  
  
## <a name="terms-and-definitions"></a>术语和定义  
 **源服务器：** 要从中迁移设置和数据的现有服务器。  
  
 **目标服务器：** 要将设置和数据迁移到的新服务器。  
  
## <a name="migration-process-summary"></a>迁移过程摘要  
 此迁移指南包括下列步骤：  
  

1.  [为 Windows Server Essentials 迁移准备源服务器](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md)。  必须确保源服务器和网络已准备好执行迁移操作。 本节指导你完成下列操作：备份源服务器，评估源服务器系统的运行状况，安装最新的 Service Pack 和修补程序，以及验证网络配置。  
  
2.  [在迁移模式下安装 Windows Server Essentials](Install-Windows-Server-Essentials-in-migration-mode.md)。  本部分介绍在迁移模式下，在目标服务器上安装 Windows Server Essentials 应执行的步骤。  
  
3.  将[计算机加入到新的 Windows Server Essentials 网络](Join-computers-to-the-new-Windows-Server-Essentials-network.md)。  本部分介绍如何将客户端计算机加入到新的 Windows Server Essentials 网络并更新组策略设置。  
  
4.  [将 Windows server 2008 Foundation 设置和数据移动到目标服务器](Move-Windows-Server-2008-Foundation-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md)。  本节提供从源服务器迁移数据和设置的相关信息。  
  
5.  [从新的 Windows Server Essentials 网络中降级和删除源服务器](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md)。  从网络中删除源服务器之前，必须强制执行组策略更新并将源服务器降级。  
  
6.  [执行 Windows Server Essentials 迁移的迁移后任务](Perform-post-migration-tasks-for-Windows-Server-Essentials-migration.md)。  完成将所有设置和数据迁移到 Windows Server Essentials 后，你可能需要将允许的计算机映射到用户帐户。  
  
7.  [运行 Windows Server Essentials 最佳做法分析器](Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md)。  在完成将设置和数据迁移到 Windows Server Essentials 后，应运行 Windows Server Essentials BPA。  

  
 某些迁移过程需要以管理员身份打开命令提示符窗口。  
  
###  <a name="to-open-a-command-prompt-window-on-the-source-server-as-an-administrator"></a><a name="BKMK_OpenACommandPromptAsAdmin"></a>在源服务器上以管理员身份打开 "命令提示符" 窗口  
  
1.  单击“启动”。  
  
2.  在搜索框中，键入“cmd”****。  
  
3.  在结果列表中，右键单击“cmd”****，然后单击“以管理员身份运行”****。  
  
#### <a name="to-open-a-command-prompt-window-on-the-destination-server-as-an-administrator"></a>在目标服务器上以管理员身份打开命令提示符窗口的步骤  
  
1.  在“开始”**** 屏幕的搜索框中，键入 **cmd**。  
  
2.  在结果列表中，右键单击“cmd”****，然后单击“以管理员身份运行”****。
