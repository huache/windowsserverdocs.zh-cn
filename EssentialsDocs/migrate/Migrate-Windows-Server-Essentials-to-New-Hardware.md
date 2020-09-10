---
title: 将 Windows Server Essentials 迁移到新硬件
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: f695ae90-3160-407b-bebf-9e460f22c86d
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 704fc7fa97c949080104846011cf07e8e28da73a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625862"
---
# <a name="migrate-windows-server-essentials-to-new-hardware"></a>将 Windows Server Essentials 迁移到新硬件

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本指南介绍如何将现有的 Windows Server &reg; 2012 Essentials 域迁移到新硬件上的 Windows Server Essentials，然后迁移设置和数据。 本指南还介绍了在完成迁移后如何从 Windows Server Essentials 网络中删除现有的服务器。

> [!NOTE]
>  为了避免迁移过程中出现问题，Windows Server Essentials 产品开发团队强烈建议你在开始迁移之前先阅读本文档。
>
> [!NOTE]
>
>  若要将服务器数据迁移到 Windows Server Essentials 的最新版本，请参阅 [迁移到 Windows Server essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)。


## <a name="additional-resources"></a>其他资源
 有关可帮助指导你完成迁移过程的其他信息、工具和社区资源的链接，请访问 [Windows Small Business Server 迁移](https://go.microsoft.com/fwlink/?LinkId=217520) 网站。

## <a name="terms-and-definitions"></a>术语和定义
 **源服务器：** 要从中迁移设置和数据的现有服务器。

 **目标服务器：** 要将设置和数据迁移到的新服务器。

## <a name="migration-process-summary"></a>迁移过程摘要
 此迁移指南包括下列步骤：


1. [为 Windows Server Essentials 迁移准备源服务器](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md)。  必须确保源服务器和网络已准备好执行迁移操作。 本节指导你完成下列操作：备份源服务器，评估源服务器系统的运行状况，安装最新的 Service Pack 和修补程序，以及验证网络配置。

2. [在迁移模式下安装 Windows Server Essentials](Install-Windows-Server-Essentials-in-migration-mode.md)。  本部分介绍在迁移模式下，在目标服务器上安装 Windows Server Essentials 应执行的步骤。

3. 将[计算机加入到新的 Windows Server Essentials 服务器](Join-computers-to-the-new-Windows-Server-Essentials-server.md)。  本部分介绍如何将客户端计算机加入到新的 Windows Server Essentials 服务器并更新组策略设置。

4. [将设置和数据移动到目标服务器以进行 Windows Server Essentials 迁移](Move-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md)。  本节提供从源服务器迁移数据和设置的相关信息。

5. [在 Windows Server Essentials 目标服务器上配置文件夹重定向](Configure-folder-redirection-on-the-Windows-Server-Essentials-Destination-Server.md)。  如果在源服务器上启用了文件夹重定向，则可以在目标服务器上也启用同样功能，然后删除旧的“文件夹重定向组策略”设置。

6. [从新的 Windows Server Essentials 网络中降级和删除源服务器](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md)。  从网络中删除源服务器之前，必须强制执行组策略更新并将源服务器降级。

7. [执行 Windows Server Essentials 迁移的迁移后任务](Perform-post-migration-tasks-for-Windows-Server-Essentials-migration.md)。  完成将所有设置和数据迁移到 Windows Server Essentials 后，你可能需要将允许的计算机映射到用户帐户。

8. [运行 Windows Server Essentials 最佳做法分析器](Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md)。  完成将设置和数据迁移到 Windows Server Essentials 后，应下载并运行 Windows Server Essentials BPA。

   某些迁移过程需要以管理员身份打开命令提示符窗口。

#### <a name="to-open-a-command-prompt-window-as-an-administrator"></a>以管理员身份打开“命令提示符”窗口的步骤

1.  在“开始”**** 屏幕的搜索框中，键入 **cmd**。

2.  在结果列表中，右键单击“cmd”****，然后单击“以管理员身份运行”****。
