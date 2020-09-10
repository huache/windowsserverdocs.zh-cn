---
title: 管理 Active Directory 管理中心中的不同域
description: Windows Server 安全
ms.assetid: 166351c3-4076-48be-aa8f-797adf1e9d68
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: c793c30c6637a050d2b2cbb055ec289e3c3e8f20
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638036"
---
# <a name="manage-different-domains-in-active-directory-administrative-center"></a>管理 Active Directory 管理中心中的不同域

>适用于：Windows Server（半年频道）、Windows Server 2016

  当你打开 Active Directory 管理 "时，你当前登录到此计算机上的域将 \( \) 出现在 Active Directory 管理中心导航窗格中的 \( 左窗格中 \) 。 根据你的当前登录凭据集的权限，可以查看或管理此本地域中的 Active Directory 对象。

 你还可以使用相同的一组登录凭据和 Active Directory 管理中心的同一个实例来查看或管理同一林中的任何其他域中的 Active Directory 对象或与本地域建立了信任关系的另一个林中的域。 同时 \- 支持单向信任和双向 \- 信任。

> [!NOTE]
>  如果域 a 和域 B 之间存在单向信任，则域 A 中的 \- 用户可以访问域 b 中的资源，但是域 b 中的用户无法访问域 a 中的资源，如果在域 a 所属的计算机上运行 Active Directory 管理中心，则可以使用当前的一组登录凭据和在同一实例 Active Directory 管理中心中连接到域 b。 但是，如果在本地域为域 B 的计算机上运行 Active Directory 管理中心，则无法在相同的 Active Directory 管理中心实例中使用相同的凭据集连接到域 A。

 不需要任何最低组成员身份即可完成此过程。

### <a name="windows-server-2012-to-manage-a-foreign-domain-in-the-selected-instance-of-active-directory-administrative-center-using-the-current-set-of-logon-credentials"></a>Windows Server 2012：使用当前登录凭据集在所选实例中管理外域 Active Directory 管理中心

1.  若要打开 Active Directory 管理中心，请在 **服务器管理器**中单击 " **工具**"，然后单击 " **Active Directory 管理中心**"。

    > [!NOTE]
    >  打开 Active Directory 管理中心的另一种方法是单击 " **开始**"，然后键入 **dsac.exe**。

2.  若要打开 " **添加导航节点**"，请单击 " **管理**"，然后单击 " **添加导航节点** "，如下图所示。

     ![显示 * * 添加导航节点的屏幕截图 * * UI](media/ADDS_ADACAddNavNode.gif)

3.  在 " **添加导航节点**" 中，单击 " **连接到其他域** "，如下图所示。

     ![显示 * * 添加导航节点的屏幕截图 * * UI](media/ADDS_ADACConnectToDomain.gif)

4.  在 "**连接到**" 中，键入要管理的外部域的名称 \( （例如**contoso.com** \) ），然后单击 **"确定"**。

5.  成功连接到外部域后，浏览 " **添加导航节点** " 窗口中的列，选择要添加到 Active Directory 管理中心导航窗格中的容器，然后单击 **"确定"**。

### <a name="windows-server-2008-r2-to-manage-a-foreign-domain-in-the-selected-instance-of-active-directory-administrative-center-using-the-current-set-of-logon-credentials"></a>Windows Server 2008 R2：使用当前登录凭据集在所选实例中管理外域 Active Directory 管理中心

1. 若要打开 Active Directory 管理中心，请单击 " **开始**"，单击 " **管理工具**"，然后单击 " **Active Directory 管理中心**"。

   > [!NOTE]
   >  打开 Active Directory 管理中心的另一种方法是依次单击 " **开始**"、" **运行**"，然后键入 **dsac.exe**。

2. 若要打开 " **添加导航节点**"，在 "Active Directory 管理中心" 窗口顶部附近，单击 " **添加导航节点** "，如下图所示。

    ![显示 * * 添加导航节点的屏幕截图 * * UI](media/click_add_nav_nodes.gif)

   > [!NOTE]
   >  打开 " **添加导航节点** " 的另一种方法是右键 \- 单击 Active Directory 管理中心导航窗格中的空白区域中的任意位置，然后单击 " **添加导航节点**"。

3. 在 " **添加导航节点**" 中，单击 " **连接到其他域** "，如下图所示。

    ![显示 * * 添加导航节点的屏幕截图 * * * 连接到其他域 * * UI](media/add_nav_nodes.gif)

4. 在 "**连接到**" 中，键入要管理的外部域的名称 \( （例如**contoso.com** \) ），然后单击 **"确定"**。

5. 成功连接到外部域后，浏览 " **添加导航节点** " 窗口中的列，选择要添加到 Active Directory 管理中心导航窗格中的容器，然后单击 **"确定"**。

   有关自定义 Active Directory 管理中心导航窗格的详细信息，请参阅 [自定义 Active Directory 管理中心导航窗格](customize-the-active-directory-administrative-center-navigation-pane.md)。

   还可以使用与当前登录凭据集不同的登录凭据集打开 Active Directory 管理中心。 如果使用普通用户凭据登录到运行 Active Directory 管理中心的计算机，但希望以管理员身份使用此计算机上的 Active Directory 管理中心来管理本地域，则以下过程中的命令可用会非常有用。 \(如果你想要使用 Active Directory 管理中心远程管理与你的本地域不同的外域，并使用一组与当前的登录凭据不同的凭据，则此命令也会很有用。 但是，外部域必须与本地域建立了信任关系。\)

   不需要任何最低组成员身份即可完成此过程。

### <a name="to-manage-a-domain-using-logon-credentials-that-are-different-from-the-current-set-of-logon-credentials"></a>使用与当前登录凭据集不同的登录凭据管理域的步骤

1.  若要打开 Active Directory 管理中心，请在命令提示符下键入以下命令，然后按 Enter：

     `runas /user:<domain\user> dsac`

     其中 `<domain\user>` ，是要用来打开 Active Directory 管理中心的凭据集，它 `dsac` 是Dsac.exe的 Active Directory 管理中心可执行文件 \( 名称 \) 。

     例如，请键入以下命令，然后按 Enter：

     `runas /user:contoso\administrator dsac`

2.  在打开 Active Directory 管理中心之后，即可浏览导航窗格以查看或管理你的 Active Directory 域。



