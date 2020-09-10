---
title: 步骤 3：将计算机加入新的 Windows Server Essentials 服务器
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: a0e07d1a-8409-429b-87d7-0f4a7e14d668
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 7495831c6f593b65261fda8f50d4ef9d1000d9b4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625485"
---
# <a name="step-3-join-computers-to-the-new-windows-server-essentials-server"></a>步骤 3：将计算机加入新的 Windows Server Essentials 服务器

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials

迁移过程的下一步是将客户端计算机连接到运行 Windows Server Essentials 的新服务器。

> [!NOTE]
>  对于运行 Windows XP 或 Windows Vista 操作系统的计算机，可以跳过此步骤。 Windows Server 连接器软件不支持运行 Windows XP 或 Windows Vista 的计算机。

 在将客户端计算机加入到新的 Windows Server Essentials 服务器之前，必须通过卸载客户端计算机上的 Windows Server 连接器软件来断开它与源服务器的连接。

### <a name="to-uninstall-windows-server-connector-on-a-client-computer"></a>卸载客户端计算机上的 Windows Server 连接器

1.  从客户端计算机打开“控制面板”，然后打开“程序和功能”****。

2.  在程序列表中，右键单击在你的计算机上运行的连接器应用程序。

    > [!NOTE]
    >  连接器应用程序可以是 **Windows Small Business Server 2011 Essentials 连接器**或 **Windows Server Essentials 连接器**，具体取决于客户端计算机连接到的 Windows Server essentials 的版本。

3.  单击“卸载”  。

### <a name="to-reconnect-a-client-computer-to-the-server"></a>将客户端计算机重新连接到服务器

1.  登录要连接到服务器的计算机。

    > [!NOTE]
    >  如果此计算机上具有多个用户帐户，则使用包含你要在将计算机连接到服务器后继续保留的文档、图片和个人首选项的用户帐户进行登录。

2.  打开 Internet 浏览器，如 Internet Explorer。

3.  在地址栏中，键入 **http://<servername \> /Connect**，然后按 enter。

4.  按照屏幕上的说明，将客户端计算机加入到新的 Windows Server Essentials 服务器。

## <a name="next-steps"></a>后续步骤
 已将客户端计算机加入运行 Windows Server Essentials 的新服务器。 现在转到 [步骤4：将设置和数据移动到目标服务器以进行 Windows Server Essentials 迁移](Step-4--Move-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md)。


若要查看所有步骤，请参阅 [迁移到 Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)。

