---
title: 将 Windows Server Essentials 添加为成员服务器
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: d09dd82f-f7d2-47ce-862d-fd9869f2021c
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 3325799dc8fb81ab15f8cb03102b9c6248526b74
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624007"
---
# <a name="add-windows-server-essentials-as-a-member-server"></a>将 Windows Server Essentials 添加为成员服务器

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本主题适用于运行 Windows server 2012 R2 Standard、Windows Server 2012 R2 Datacenter 或 Windows server 2016 （安装了 Windows Server Essentials Experience 角色）的服务器。 在本文档的其余部分中，将 Windows Server Essentials 体验角色称为 Windows Server Essentials。

> [!NOTE]
>   Windows Server Essentials 只能部署为域控制器。 在本文档中，Windows Server Essentials 不包括 Windows Server Essentials。

 不需要将 Windows Server Essentials 作为 Windows 域内的主服务器。 可以将 Windows Server Essentials 作为成员服务器添加到现有 Active Directory 域环境中，并充分利用它所提供的简单数据保护、安全远程访问和云集成功能。 此外，Windows Server Essentials 可以部署在现有 Active Directory 环境中，而不必作为域控制器。 这使你可以针对本地存储和管理来扩展存储或使用分支机构。

 你可以在以下情况中添加 Windows Server Essentials：

-   在分支机构位置添加 Windows Server Essentials，并使用本机工具将它加入到位于总部（在不同的位置）的域控制器中。 可以在此成员服务器上打开 BranchCache 功能以达到最佳带宽利用率。

-   将 Windows Server Essentials 添加为 Windows Server Essentials 网络中的成员服务器，以通过在成员服务器上添加其他服务器文件夹来帮助扩展网络上的存储。

-   如果运行 Windows Server Essentials 的主服务器托管在 Microsoft Azure 中或由第三方主机托管，请将 Windows Server Essentials 添加为本地办公室中的成员服务器。 在本地办公室站点将 Windows Server Essentials 作为成员服务器有助于优化带宽使用率。

## <a name="adding-windows-server-essentials-as-a-member-server"></a>将 Windows Server Essentials 添加为成员服务器
 若要将 Windows Server Essentials 作为成员服务器添加到现有 Active Directory 环境中运行 Windows Server 2012 R2 或 Windows Server Essentials 的主服务器，则必须完成以下步骤：

1.  将运行 Windows Server Essentials 的服务器加入工作组。

2.  将运行 Windows Server Essentials 的服务器加入到主 Windows Server Essentials 服务器的域中。

3.  从服务器管理器配置 Windows Server Essentials Experience。

#### <a name="to-join-windows-server-essentials-to-a-workgroup-or-domain"></a>将 Windows Server Essentials 加入工作组或域

1. 在第二台服务器上完成 Windows Server Essentials 的安装后，关闭配置 Windows Server Essentials 向导。

2. 在“搜索”**** 框中，键入 **System Settings**，然后在搜索结果中，单击“查看高级系统设置”****。

3. 在“系统属性”**** 中，单击“计算机名称”**** 选项卡。

4. 在“计算机名称”**** 的“域”**** 部分中，单击“更改”****。

5. 在 " **计算机名/域更改**" 的 " **成员** " 部分中，选择是否要将运行 Windows server Essentials 的服务器加入 **工作组** 或 **域**。

   -   若要将服务器添加到工作组，请键入 **workgroup**，然后单击“确定”****。

   -   若要将此服务器加入到现有 Active Directory 域，请键入域的名称，然后单击“确定”****。

6. 重启服务器以应用更改。

   将服务器加入到主服务器的域之后，可以通过从服务器管理器运行配置 Windows Server Essentials 向导来继续配置 Windows Server Essentials。

#### <a name="to-configure-windows-server-essentials-experience-on-a-member-server"></a>在成员服务器上配置 Windows Server Essentials 体验

1.  （可选）更改服务器名称（如果需要）。

    > [!IMPORTANT]
    >  配置 Windows Server Essentials 体验后，不能更改服务器名称。

2.  使用域管理员帐户登录到服务器。

3.  打开服务器管理器。

4.  在“服务器管理器”**** 中的标志通知区域内，单击标志，然后单击“配置 Windows Server Essentials”****。

5.  选择将服务器配置为成员服务器，然后单击“下一步”****。

6.  单击“配置”**** 以开始进行配置。 完成配置过程需要大约 10 分钟的时间。

7.  在桌面上，单击仪表板图标以启动服务器仪表板。 在“主页”上，完成“安装”**** 选项卡上列出的“入门”**** 任务。

## <a name="additional-references"></a>其他参考


-   [安装 Windows Server Essentials](Install-Windows-Server-Essentials.md)

-   [安装 Windows Server Essentials](../install/Install-Windows-Server-Essentials.md)

