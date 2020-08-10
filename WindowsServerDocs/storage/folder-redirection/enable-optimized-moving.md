---
title: 启用重定向文件夹的优化移动
description: 如何执行重定向文件夹到新文件共享的优化移动。
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.date: 09/10/2018
ms.localizationpriority: medium
ms.openlocfilehash: 895bf41a5a42bd4578e99ba12205b56da18b9ba2
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87942187"
---
# <a name="enable-optimized-moves-of-redirected-folders"></a>启用重定向文件夹的优化移动

>适用于：Windows 10、Windows 8、Windows 8.1、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server（半年频道）

本主题介绍如何执行重定向文件夹（文件夹重定向）到新文件共享的优化移动。 如果启用此策略设置，当管理员移动托管重定向文件夹的文件共享并更新组策略中重定向文件夹的目标路径时，只需在本地脱机文件缓存中重命名缓存内容，而不会出现任何延迟或用户数据丢失。

以前，管理员可以在组策略中更改重定向文件夹的目标路径，并让客户端计算机在受影响的用户下次登录时复制文件，从而导致登录延迟。 或者管理员可以移动文件共享，并更新组策略中重定向文件夹的目标路径。 但是从移动后开始到移动后第一次同步，客户端计算机上所进行的任何更改都将丢失。

## <a name="prerequisites"></a>必备条件

优化移动具有下列要求：

- 必须设置文件夹重定向。 有关详细信息，请参阅[部署文件夹重定向和脱机文件](deploy-folder-redirection.md)。
- 客户端计算机必须运行 Windows 10、Windows 8.1、Windows 8、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 或 Windows Server （半年频道）。

## <a name="step-1-enable-optimized-move-in-group-policy"></a>步骤 1：在组策略中启用优化移动

若要优化文件夹重定向数据的重定位，请使用组策略启用“在文件夹重定向服务器路径更改时对脱机文件缓存中的内容启用优化移动”策略设置，以用于适当的组策略对象 (GPO)  。 将此策略设置配置为“禁用”或“未配置”会使客户端将所有文件夹重定向内容复制到新位置，然后在服务器路径更改时从旧位置删除内容   。

下面介绍了如何启用重定向文件夹的优化移动：

1. 在“组策略管理”中，右键单击为文件夹重定向设置（例如“文件夹重定向”和“漫游用户策略文件设置”）所创建的 GPO，然后选择“编辑”   。
2. 在“用户配置”下，依次导航到“策略”、“管理模板”、“系统”、“文件夹重定向”      。
3. 右键单击“在文件夹重定向服务器路径更改时对脱机文件缓存中的内容启用优化移动”，然后选择“编辑”   。
4. 选择“已启用”，然后选择“确定”   。

## <a name="step-2-relocate-the-file-share-for-redirected-folders"></a>步骤 2：重定位重定向文件夹的文件共享

当移动包含用户重定向文件夹的文件共享时，请务必采取预防措施来确保正确地重新定位文件夹。

>[!IMPORTANT]
>如果用户的文件正在使用中，或者如果移动时未保留完整的文件状态，则当通过网络复制文件时，用户可能会遇到性能不佳、脱机文件产生的同步冲突、甚至数据丢失问题。

1. 提前通知用户，托管其重定向文件夹的服务器将发生更改，并建议他们执行以下操作：

      - 同步其脱机文件缓存的内容并解决所有冲突。
      - 打开提升的命令提示符，输入 GpUpdate /Target:User /Force，然后注销并重新登录，以确保将最新的组策略设置应用于客户端计算机 

        >[!NOTE]
        >默认情况下，客户端计算机每 90 分钟更新一次组策略，因此，如果你为客户端计算机提供了足够的时间来接收更新的策略，则无需让用户使用 GpUpdate  。
2. 从服务器中删除文件共享，以确保不会使用文件共享中的文件。 为此，请在“服务器管理器”中的文件和存储服务的“共享”页上，右键单击相应的文件共享，然后选择“删除”   。

    用户将使用脱机文件脱机工作，直到移动完成，并收到组策略的已更新文件夹重定向设置。

3. 使用具有备份权限的帐户，通过保留文件时间戳的方法（如备份和还原实用程序）将文件共享的内容移到新位置。 若要使用 Robocopy 命令，请打开提升的命令提示符，然后键入以下命令，其中 ```<Source>``` 为文件共享的当前位置，```<Destination>``` 为新位置  ：

    ```PowerShell
    Robocopy /B <Source> <Destination> /Copyall /MIR /EFSRAW
    ```

    >[!NOTE]
    >Xcopy 命令不会保留所有文件状态  。
4. 编辑文件夹重定向策略设置，更新每个要重新定位的重定向文件夹的目标文件夹位置。 有关详细信息，请参阅[部署文件夹重定向和脱机文件](deploy-folder-redirection.md)的步骤 4。
5. 通知用户托管其重定向文件夹的服务器已更改，并应使用 GpUpdate /Target:User /Force 命令，然后注销并重新登录，从而获取更新的配置并恢复正确的文件同步  。

    用户至少应登录一次到所有计算机，以确保数据在每个脱机文件缓存中正确地重新定位。

## <a name="more-information"></a>详细信息

* [部署文件夹重定向和脱机文件](deploy-folder-redirection.md)
* [部署漫游用户配置文件](deploy-roaming-user-profiles.md)
* [文件夹重定向、脱机文件和漫游用户策略文件概述](folder-redirection-rup-overview.md)