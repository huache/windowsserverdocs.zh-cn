---
title: 从早期版本迁移到 Windows Server Essentials 或 Windows Server Essentials 体验
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.topic: article
ms.assetid: 2974fb3a-5150-43fd-a73f-3e5074eb5d03
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: f58a8f83fed4185ee51145b988cfef1074f889c7
ms.sourcegitcommit: e817a130c2ed9caaddd1def1b2edac0c798a6aa2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2019
ms.locfileid: "74945141"
---
# <a name="migrate-from-previous-versions-to-windows-server-essentials-or-windows-server-essentials-experience"></a>从早期版本迁移到 Windows Server Essentials 或 Windows Server Essentials 体验

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本指南介绍如何从以前版本的 Windows Small Business Server 和 Windows Server Essentials （包括 Windows Server Essentials、Windows Small Business Server 2011 Standard、Windows Small Business Server 2011 Essentials、WindowsWindows server Essentials 或 windows server 2012 R2 （安装了 Windows Server Essentials Experience 角色）到 Windows server Essentials 或 Windows Server R2 的 Small Business Server 2008 和 Windows Small Business Server 2003）。  
  
 **对于具有最多25个用户和50设备的环境**，你可以按照本指南中的步骤从早期版本的 windows SBS 迁移到 Windows Server Essentials。  
  
 **对于最多包含100个用户和200台设备的环境**，你可以按照相同的指南迁移到安装了 Windows Server Essentials 体验角色的 windows Server 2012 R2 标准版或数据中心版。  
  
> [!NOTE]
>  为了避免迁移过程中出现问题，Windows Server Essentials 产品开发团队强烈建议你在开始迁移之前先阅读本文档。  
  
## <a name="terms-and-definitions"></a>术语和定义  
 **源服务器** 作为迁移设置和数据的来源的现有服务器。  
  
 **目标服务器** 作为迁移设置和数据的目标的新服务器。  
  
## <a name="migration-process-summary"></a>迁移过程摘要  
 此迁移指南包括下列步骤：  
  
1. [步骤1：为 Windows Server Essentials 迁移准备源服务器](Step-1--Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md)。  必须确保源服务器和网络已准备好执行迁移操作。 本节指导你完成下列操作：备份源服务器，评估源服务器系统的运行状况，安装最新的 Service Pack 和修补程序，以及验证网络配置。  
  
2. [步骤2：将 Windows Server Essentials 作为新的副本域控制器进行安装](Step-2--Install-Windows-Server-Essentials-as-a-new-replica-domain-controller.md)。 本部分介绍如何将 Windows server Essentials 或 Windows Server 2012 R2 Standard （启用 Windows Server Essentials Experience 角色）安装为域控制器。  
  
3. [步骤3：将计算机加入到新的 Windows Server Essentials 服务器](Step-3--Join-computers-to-the-new-Windows-Server-Essentials-server.md)。  本部分介绍如何将客户端计算机加入到运行 Windows Server Essentials 的新服务器并更新组策略设置。  
  
4. [步骤4：将设置和数据移动到目标服务器以进行 Windows Server Essentials 迁移](Step-4--Move-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md)。  本节提供从源服务器迁移数据和设置的相关信息。  
  
5. [步骤5：在目标服务器上启用文件夹重定向以进行 Windows Server Essentials 迁移](Step-5--Enable-folder-redirection-on-the-Destination-Server-for-Windows-Server-Essentials-migration.md)。  如果在源服务器上启用了文件夹重定向，则可以在目标服务器上也启用同样功能，然后删除旧的“文件夹重定向组策略”设置。  
  
6. [步骤6：从新的 Windows Server Essentials 网络中降级和删除源服务器](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md)。  从网络中删除源服务器之前，必须强制执行组策略更新并将源服务器降级。  
  
7. [步骤7：执行 Windows Server Essentials 迁移的迁移后任务](Step-7--Perform-post-migration-tasks-for-the-Windows-Server-Essentials-migration.md)。  完成将所有设置和数据迁移到 Windows Server Essentials 后，你可能需要将允许的计算机映射到用户帐户。  
  
8. [步骤8：运行 Windows Server Essentials 最佳做法分析器](Step-8--Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md)。  在完成将设置和数据迁移到 Windows Server Essentials 后，应运行 Windows Server Essentials 最佳做法分析器（BPA）。  
  
   某些迁移过程需要以管理员身份打开命令提示符窗口。 以下过程介绍如何执行此操作。  
  
###  <a name="BKMK_OpenACommandPromptAsAdmin"></a>在源服务器上以管理员身份打开 "命令提示符" 窗口  
  
1.  单击**开始**。  
  
2.  在搜索框中，键入“cmd”。  
  
3.  在结果列表中，右键单击“cmd”，然后单击“以管理员身份运行”。  
  
#### <a name="to-open-a-command-prompt-window-on-the-destination-server-as-an-administrator"></a>在目标服务器上以管理员身份打开命令提示符窗口的步骤  
  
1.  在“开始”屏幕的搜索框中，键入 **cmd**。  
  
2.  在结果列表中，右键单击“cmd”，然后单击“以管理员身份运行”。  
  
## <a name="see-also"></a>另请参阅  
  
-   [将服务器数据迁移到 Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

-   [将服务器数据迁移到 Windows Server Essentials](../migrate/Migrate-Server-Data-to-Windows-Server-Essentials.md)

