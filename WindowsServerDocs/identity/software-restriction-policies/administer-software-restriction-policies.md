---
title: 管理软件限制策略
description: Windows Server 安全
ms.topic: article
ms.assetid: 8cc22093-67d1-47b6-9ddd-4569b6761ce9
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: b67464b2a1b1d9f1828afc7885ddd8e18116c1d6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637877"
---
# <a name="administer-software-restriction-policies"></a>管理软件限制策略

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

适用于 IT 专业人员的本主题介绍了如何使用软件限制策略（从 Windows Server 2008 和 Windows Vista 开始)  (SRP）来管理应用程序控制策略。

## <a name="introduction"></a>简介
软件限制策略 (SRP) 是基于组策略的功能，用于标识在域中的计算机上运行的软件程序，以及控制这些程序的运行能力。 你可以使用软件限制策略创建计算机的高度受限配置，从而仅允许运行专门标识的应用程序。 它们与 Microsoft Active Directory 域服务和组策略集成在一起，但也可以在独立计算机上进行配置。 有关 SRP 的详细信息，请参阅 [软件限制策略](software-restriction-policies.md)。

从 Windows Server 2008 R2 和 Windows 7 开始，可以使用 Windows AppLocker，而不是与 SRP 一起使用，以获得部分应用程序控制策略。

本主题包含：

-   [打开软件限制策略](#BKMK_Open_SRP)

-   [创建新的软件限制策略](#BKMK_Create_SRP)

-   [添加或删除指定的文件类型](#BKMK_Add_Del)

-   [防止软件限制策略应用于本地管理员](#BKMK_Prevent_Admin)

-   [更改软件限制策略的默认安全级别](#BKMK_Sec_Lvl)

-   [将软件限制策略应用于 Dll](#BKMK_Apply_SRP_DLLs)

有关如何使用 SRP 完成特定任务的信息，请参阅以下内容：

-   [确定软件限制策略的允许-拒绝列表和应用程序清单](determine-allow-deny-list-and-application-inventory-for-software-restriction-policies.md)

-   [使用软件限制策略规则](work-with-software-restriction-policies-rules.md)

-   [使用软件限制策略来帮助保护你的计算机免受电子邮件病毒侵害](use-software-restriction-policies-to-help-protect-your-computer-against-an-email-virus.md)

## <a name="to-open-software-restriction-policies"></a><a name="BKMK_Open_SRP"></a>打开软件限制策略

-   [对于本地计算机](#BKMK_1)

-   [对于域、站点或组织单位，并且位于加入到域中的成员服务器或工作站上](#BKMK_2)

-   [对于域或组织单位，并且位于安装了远程服务器管理工具的域控制器或工作站上](#BKMK_3)

-   [对于站点，你位于域控制器或安装了远程服务器管理工具的工作站上](#BKMK_4)

### <a name="for-your-local-computer"></a><a name="BKMK_1"></a>对于本地计算机

1.  打开“本地安全设置”。

2.  在控制台树中，单击 " **软件限制策略**"。

    **其中?**

    -   安全设置/软件限制策略

> [!NOTE]
> 若要执行该过程，你必须是本地计算机上 Administrators 组的成员，或你必须已被委派适当的权限。

### <a name="for-a-domain-site-or-organizational-unit-and-you-are-on-a-member-server-or-on-a-workstation-that-is-joined-to-a-domain"></a><a name="BKMK_2"></a>对于域、站点或组织单位，并且位于加入到域中的成员服务器或工作站上

1.  打开 Microsoft 管理控制台 (MMC)。

2.  在 " **文件** " 菜单上，单击 " **添加/删除管理单元**"，然后单击 " **添加**"。

3.  单击“本地组策略对象编辑器”，然后单击“添加”********。

4.  在“选择组策略对象”**** 中单击“浏览”****。

5.  在 " **浏览组策略对象**" 中，选择相应域、站点或组织单位中 (GPO) 的组策略对象，或创建一个新的对象，然后单击 " **完成**"。

6.  单击“关闭”****，然后单击“确定”****。

7.  在控制台树中，单击 " **软件限制策略**"。

    **其中?**

    -   *组策略对象* [*ComputerName*] 策略/计算机配置或

        用户配置/Windows 设置/安全设置/软件限制策略

> [!NOTE]
> 若要执行此过程，您必须是 Domain Admins 组的成员。

### <a name="for-a-domain-or-organizational-unit-and-you-are-on-a-domain-controller-or-on-a-workstation-that-has-the-remote-server-administration-tools-installed"></a><a name="BKMK_3"></a>对于域或组织单位，并且位于安装了远程服务器管理工具的域控制器或工作站上

1.  打开组策略管理控制台。

2.  在控制台树中，右键单击要为其打开软件限制策略的组策略对象 ("GPO) "。

3.  单击“编辑”打开要编辑的 GPO****。 也可以单击“新建”以创建一个新的 GPO，然后单击“编辑”********。

4.  在控制台树中，单击 " **软件限制策略**"。

    **其中?**

    -   *组策略对象* [*ComputerName*] 策略/计算机配置或

        用户配置/Windows 设置/安全设置/软件限制策略

> [!NOTE]
> 若要执行此过程，您必须是 Domain Admins 组的成员。

### <a name="for-a-site-and-you-are-on-a-domain-controller-or-on-a-workstation-that-has-the-remote-server-administration-tools-installed"></a><a name="BKMK_4"></a>对于站点，你位于域控制器或安装了远程服务器管理工具的工作站上

1.  打开组策略管理控制台。

2.  在控制台树中，右键单击要为其设置组策略的站点。

    **其中?**

    -   Active Directory 站点和服务 [*Domain_Controller_Name. Domain_Name*]/Sites/Site

3.  单击 " **组策略对象链接** " 中的条目以选择现有组策略对象 (GPO) ，然后单击 " **编辑**"。 也可以单击“新建”以创建一个新的 GPO，然后单击“编辑”********。

4.  在控制台树中，单击 " **软件限制策略**"。

    **Where**

    -   *组策略对象* [*ComputerName*] 策略/计算机配置或

        用户配置/Windows 设置/安全设置/软件限制策略

> [!NOTE]
> -   若要执行该过程，你必须是本地计算机上 Administrators 组的成员，或你必须已被委派适当的权限。 如果计算机已加入域，则 Domain Admins 组的成员也许能够执行该过程。
> -   若要设置应用于计算机的策略设置，而不考虑哪些用户登录到计算机，请单击 " **计算机配置**"。
> -   若要设置应用于用户的策略设置，而不考虑登录到的计算机，请单击 " **用户配置**"。

## <a name="to-create-new-software-restriction-policies"></a><a name="BKMK_Create_SRP"></a>创建新的软件限制策略

1.  打开“软件限制策略”。

2.  在“操作”菜单上单击“新建软件限制策略”********。

> [!WARNING]
> -   需要根据你的环境，使用不同的管理凭据来执行此过程：
>
>     -   如果为本地计算机创建新的软件限制策略：本地 **Administrators** 组中的成员身份或等效身份是完成此过程所需的最低要求。
>     -   如果要为加入到域的计算机创建新的软件限制策略，则域管理员组的成员可以执行此过程。
> -   如果已经为组策略对象 (GPO) 创建了软件限制策略，则“操作”菜单上不会显示“新建软件限制策略”命令********。 若要删除已应用到 GPO 的软件限制策略，请在控制台树中，右键单击“软件限制策略”，然后单击“删除软件限制策略”********。 删除 GPO 的软件限制策略时，还会删除该 GPO 的所有软件限制策略规则。 在删除软件限制策略后，可为该 GPO 创建新的软件限制策略。

## <a name="to-add-or-delete-a-designated-file-type"></a><a name="BKMK_Add_Del"></a>添加或删除指定的文件类型

1.  打开“软件限制策略”。

2.  在详细信息窗格中，双击“指定的文件类型”****。

3.  执行下列操作之一：

    -   若要添加文件类型，请在“文件扩展名”中键入文件扩展名，然后单击“添加”********。

    -   若要删除文件类型，请在“指定的文件类型”中单击文件类型，然后单击“删除”********。

> [!NOTE]
> -   需要根据你在其中添加或删除指定文件类型的环境，使用不同的管理凭据执行此过程：
>
>     -   如果为本地计算机添加或删除指定的文件类型：本地 **Administrators** 组中的成员身份或等效身份是完成此过程所需的最低要求。
>     -   如果要为加入到域的计算机创建新的软件限制策略，则域管理员组的成员可以执行此过程。
> -   可能需要为组策略对象 (GPO) 创建新的软件限制策略设置（如果尚未这样做）。
> -   指定文件类型的列表由 GPO 的计算机配置和用户配置的所有规则共享。

## <a name="to-prevent-software-restriction-policies-from-applying-to-local-administrators"></a><a name="BKMK_Prevent_Admin"></a>防止软件限制策略应用于本地管理员

1.  打开“软件限制策略”。

2.  在详细信息窗格中，双击“强制”****。

3.  在“将软件限制策略应用于以下用户”下，单击“除本地管理员以外的所有用户”********。

> [!WARNING]
> -   必须至少具有本地 **Administrators** 组中的成员身份或同等身份才能完成此过程。
> -   可能需要为组策略对象 (GPO) 创建新的软件限制策略设置（如果尚未这样做）。
> -   如果用户成为组织中计算机上的本地 Administrators 组成员的情况很常见，则你可能不需要启用此选项。
> -   如果要为本地计算机定义软件限制策略设置，请使用此过程来防止向本地管理员应用软件限制策略。 如果要为你的网络定义软件限制策略设置，请通过组策略根据安全组中的成员身份筛选用户策略设置。

## <a name="to-change-the-default-security-level-of-software-restriction-policies"></a><a name="BKMK_Sec_Lvl"></a>更改软件限制策略的默认安全级别

1.  打开“软件限制策略”。

2.  在详细信息窗格中，双击“安全级别”****。

3.  右键单击要设置为默认安全级别的安全级别，然后单击“设为默认”****。

> [!CAUTION]
> 在某些目录中，将默认安全级别设置为“不允许”可能会给操作系统造成不利影响****。

> [!NOTE]
> -   需要根据你要为其更改软件限制策略默认安全级别的环境，使用不同的管理凭据执行此过程。
> -   可能需要为此组策略对象 (GPO) 创建新的软件限制策略设置（如果尚未这样做）。
> -   在详细信息窗格中，当前的默认安全级别以一个含有复选标记的黑圈表示。 如果右键单击当前的默认安全级别，菜单中不会显示“设为默认”命令****。
> -   创建软件限制策略规则以指定默认安全级别的例外。 当默认安全级别设置为“不受限”时，规则可以指定不允许运行的软件****。 当默认安全级别设置为“不允许”时，规则可以指定允许运行的软件****。
> -   在安装时，针对系统上所有文件的软件限制策略默认安全级别设置为“不受限”****。

## <a name="to-apply-software-restriction-policies-to-dlls"></a><a name="BKMK_Apply_SRP_DLLs"></a>将软件限制策略应用于 Dll

1.  打开“软件限制策略”。

2.  在详细信息窗格中，双击“强制”****。

3.  在“将软件限制策略应用于以下”下，单击“所有软件文件”********。

> [!NOTE]
> -   若要执行该过程，你必须是本地计算机上 Administrators 组的成员，或你必须已被委派适当的权限。 如果计算机已加入域，则 Domain Admins 组的成员也许能够执行该过程。
> -   默认情况下，软件限制策略不检查动态链接库 (DLL)。 检查 DLL 可能会降低系统性能，因为每加载一个 DLL 都必须评估软件限制策略。 但是，如果你担心会接收到针对 DLL 的病毒，则可以要求检查 DLL。 如果默认安全级别设置为 "不 **允许**"，并且启用了 dll 检查，则必须创建允许每个 DLL 运行的软件限制策略规则。


