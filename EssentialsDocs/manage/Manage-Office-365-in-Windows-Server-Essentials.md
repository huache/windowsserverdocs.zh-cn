---
title: 管理 Windows Server Essentials 中的 Microsoft 365
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 3f8485e4-e10f-4f38-8a5e-d5227abd0d84
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 71e8204c8b11f423871f890badffdfb96206feb8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623067"
---
# <a name="manage-microsoft-365-in-windows-server-essentials"></a>管理 Windows Server Essentials 中的 Microsoft 365

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

将 Windows Server Essentials 服务器与 Microsoft 365 集成时，可以从 Windows Server Essentials 仪表板管理你的 Microsoft 365 服务和联机帐户以及本地资源。 在本主题中，你将了解你可以通过将服务器与 Microsoft 365、如何实现，以及如何管理和解决你的 Microsoft 365 集成来获得哪些内容。



> [!IMPORTANT]
>   Microsoft 365 集成仅在单个域控制器环境中受支持。 此外，Microsoft 365 集成向导必须在域控制器上运行。

## <a name="in-this-topic"></a>本主题内容

-   [为什么应将 Microsoft 365 与我的服务器集成？](#BKMK_IntegrationOverview)

-   [设置 Microsoft 365 集成](Manage-Office-365-in-Windows-Server-Essentials.md#BKMK_Configure)

-   [管理 Microsoft 365 集成](#BKMK_ManageIntegration)

-   [Microsoft 365 集成故障排除](Manage-Office-365-in-Windows-Server-Essentials.md#BKMK_Troubleshoot)

##  <a name="why-should-i-integrate-microsoft-365-with-my-server"></a><a name="BKMK_IntegrationOverview"></a> 为什么应将 Microsoft 365 与我的服务器集成？
 将 Microsoft 365 集成到 Windows Server Essentials 服务器有很多充分的理由。 如果你在内部管理某些资源但将 Microsoft 365 用于其他服务，你将能够从仪表板管理你的 Microsoft 365 服务和资源以及本地资源，而无需在两个位置进行操作。

- 管理使你的用户能够访问 Microsoft 365 以及你的用户帐户的联机帐户：

  -   在单个步骤中为用户创建 Microsoft Online Services 帐户，或在服务器上为现有联机帐户创建用户帐户。 你还可以向新的或现有的用户帐户添加联机帐户。

       当你从仪表板创建联机帐户时，用户将使用在服务器上使用的相同密码登录到 Microsoft 365。 如果用户更改该用户帐户的密码，则联机密码也将随之更改。 而且你知道他们的联机帐户密码始终满足你为用户帐户设置的安全要求。

  -   在用户帐户的整个生命周期内，将联机帐户与用户帐户一起管理。 如果停用用户帐户，则联机帐户也将停用。 如果删除用户帐户，则联机帐户也将随之删除。

  -   在 Windows Server Essentials 服务器上，还可以管理用于电子邮件的 Exchange Online 通讯组。

- 从组织的 Internet 域发送和接收电子邮件 (例如，通过将自定义 Internet 域链接到 Microsoft 365 订阅来) contoso.com。

- 从仪表板管理你的订阅和 Microsoft 365 集成。

- 如果你的订阅包括 SharePoint Online 库，Microsoft 365 与 Windows Server Essentials 服务器集成，你可以：

  - 从仪表板创建和管理 SharePoint Online 库。

    > [!NOTE]
    >  你还可以在你的便携式计算机、移动设备或 Windows phone 上使用 My Server 2012 R2 应用处理 SharePoint Online 库中的文档。 此功能仅适用于 Windows Server Essentials。 有关详细信息，请参阅 [使用 My Server 应用](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)。

  - 更改仪表板中 SharePoint Online 团队网站的权限，或从仪表板打开该团队网站以进行其他更改。

    有关详细信息，请参阅 [管理 SharePoint Online](Manage-SharePoint-Online-in-Windows-Server-Essentials.md)。

- 如果你订阅 Exchange Online，Microsoft 365 与 Windows Server Essentials 服务器集成，你可以管理用户用于连接到公司电子邮件服务器的移动设备：

  -   当移动设备连接到公司电子邮件服务器时，需要密码保护。 设置最小密码长度、允许登录尝试失败的次数，以及两次登录尝试之间所需的最短时间。

  -   如果你知道该设备型号存在安全问题，请阻止此类移动设备连接到 Exchange Online。

  -   如果移动设备丢失或被盗，请擦除该设备，以在该设备下次被打开时删除任何敏感的公司数据。

- Microsoft 365 集成提供了连接到 Microsoft 365 服务和资源的新方法：

  -   在 Windows Server Essentials 快速启动板中打开 Microsoft 365 的服务。 有关信息，请参阅 [使用 Microsoft 365 快速入门指南](../use/Quick-Start-Guide-to-Using-Microsoft-Office-365-with-Windows-Server-Essentials.md)。

  -   使用 My Server 2012 R2 应用从便携式计算机、移动设备或 Windows phone 使用 SharePoint Online 库中的文档。 有关信息，请参阅 [使用 My Server 应用](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)。 此功能仅在 Windows Server Essentials 中可用。

##  <a name="set-up-microsoft-365-integration"></a><a name="BKMK_Configure"></a> 设置 Microsoft 365 集成
 完成服务器安装后，你可以随时将服务器与 Microsoft 365 集成。 如果还没有 Microsoft 365 订阅，可以购买一个或注册一个免费试用订阅。

 你将执行以下任务：

-   [步骤1：验证 Microsoft 365 集成要求](#BKMK_StepOne_VERIFY)

-   [步骤2：将服务器与 Microsoft 365 集成](#BKMK_StepTwo)

-   [步骤3：将组织的 Internet 域名链接到 Microsoft 365 (可选) ](#BKMK_StepThree)

###  <a name="step-1-verify-microsoft-365-integration-requirements"></a><a name="BKMK_StepOne_VERIFY"></a> 步骤1：验证 Microsoft 365 集成要求
 在开始之前，请确保服务器满足以下要求：

-   服务器可以具有以下任一操作系统： Windows Server Essentials、Windows Server Essentials、Windows server 2012 R2 Standard 或 windows server 2012 R2 Datacenter 操作系统，并安装了 Windows Server Essentials Experience 角色。

-   该环境只能有一个域控制器，并且你必须在域控制器上执行 Microsoft 365 集成。

-   你必须能够从服务器连接到 Internet。

-   开始 Microsoft 365 集成之前，你应该在服务器上安装所有关键更新和重要更新。

-   如果你想要在电子邮件地址中使用组织的 Internet 域，并使用 SharePoint Online 资源，则需要注册域名，以便在集成期间可以将域链接到 Microsoft 365。 有关详细信息，请参阅 [如何购买域名](https://office.microsoft.com/office365-suite-help/how-to-buy-a-domain-name-HA102819883.aspx?CTT=5&origin=HA102818660)。

> [!NOTE]
>  无需提前订阅 Microsoft 365。 在 Microsoft 365 集成期间，你将能够购买订阅或注册免费试用版。 若要查看 Microsoft 365 的计划和定价，请 [比较企业 Microsoft 365 计划](https://office.microsoft.com/compare-office-365-for-business-plans-FX102918419.aspx?CR_CC=200061904&WT.srch=1&WT.mc_ID=PS_bing_O365Comm_subscribe-to-office-365_Text)。

###  <a name="step-2-integrate-the-server-with-microsoft-365"></a><a name="BKMK_StepTwo"></a> 步骤2：将服务器与 Microsoft 365 集成
 在域控制器上执行以下过程，将 Windows Server Essentials 服务器与 Microsoft 365 集成。

> [!NOTE]
>  无论你是使用 Windows Server Essentials 还是 Windows Server Essentials，此过程都是相同的，但你将从主页上的不同位置启动。 在 Windows Server Essentials 中，在 " **服务** " 选项卡上将服务器与 Microsoft 365 和其他 Microsoft Online Services 集成。在 Windows Server Essentials 中，Microsoft 365 在 " **电子邮件** " 选项卡上执行集成。

##### <a name="to-integrate-the-server-with-microsoft-365"></a>将服务器与 Microsoft 365 集成

1. 以管理员身份登录服务器，然后打开 Windows Server Essentials 仪表板。

2. 在 " **主页** " 页上，依次单击 " **服务** " (在 Windows Server Essentials 中，单击 " **电子邮件**) ，单击" **与 Microsoft 365 集成**"，然后单击" **设置 Microsoft 365 集成**"。

    此时将显示 "与 Microsoft 365 集成" 向导。

3. 在“入门”**** 页上，执行以下操作之一：

   -   如果你没有 Microsoft 365 的订阅，请单击 " **下一步**"，然后按照说明订阅 Microsoft 365 或注册试用版订阅。

        在返回到向导之前，你需要登录到 Microsoft 365。 但不需要执行 Microsoft 365 门户的 " **从这里开始** " 部分中的任何任务。

   -   如果你已有要与服务器集成的 Microsoft 365 的订阅，请选择 " **我已有 Microsoft 365 的订阅**"，然后单击 " **下一步**"。

4. 按照说明完成向导。

   向导成功完成后，你会注意到仪表板的以下更改：

-   有一个新的 **Microsoft 365** 页面，用于管理集成和你的 Microsoft 365 订阅。

-   在 " **用户** " 页上，你将看到 " **联机帐户** " 选项卡，你可以在其中创建和管理使你的用户能够访问 Microsoft 365 的 Microsoft Online Services 帐户。 如果你使用的是 Exchange Online 并且具有 Windows Server Essentials 服务器，你还将看到 " **通讯组** " 选项卡。

-   Windows Server Essentials 服务器上的 " **存储** " 页具有 " **sharepoint 库** " 选项卡，用于管理 sharepoint Online 库和更改团队网站的权限。 Microsoft 365 的每个业务计划都包括这些基本 SharePoint 联机功能。

###  <a name="step-3-link-your-organizations-internet-domain-name-to-microsoft-365-optional"></a><a name="BKMK_StepThree"></a> 步骤3：将组织的 Internet 域名链接到 Microsoft 365 (可选) 
 如果要在发送到组织的电子邮件和 SharePoint Online 资源的 Url 中使用自己的 Internet 域，可以将自定义域链接到 Microsoft 365 订阅。 如果将 Windows Server Essentials 服务器与 Microsoft 365 集成，则可以从仪表板执行此操作。

 在为用户创建联机帐户之前执行此操作最为简单，这样你就可以在批量创建联机帐户时使用域。

 注册 Microsoft 365 时，会获得*域名，例如 onmicrosoft.com。* 如果要使用不同的域名，只需 contoso.com 即可。 如果还没有域名，则需要购买一个域名，然后更改一些 DNS 记录。

 设置要与 Microsoft 365 一起使用的自定义域涉及以下四个任务：

1. **购买一个域名。** 即，通过域注册机构或 DNS 托管提供者对其进行注册。

   -   选择与 Microsoft 365 一起使用的域名。 可以使用二级域名（例如，buycontoso.com？，而不能使用第三级域名，例如 marketing.contoso.com）。 有关选择要在 Microsoft 365 中使用的域的详细信息，请参阅 [域](/office365/servicedescriptions/office-365-platform-service-description/domains)。

   -   从允许域名服务器 (DNS 的域注册机构购买它) Microsoft 365 所需的记录。 若要查明哪些域注册机构允许所需的 DNS 记录，请参阅 [如何购买域名](https://office.microsoft.com/office365-suite-help/how-to-buy-a-domain-name-HA102819883.aspx?CTT=5&origin=HA102818660)。 如果你已经使用其他注册机构注册了你的域，请不要担心;当你将域链接到 Microsoft 365 时，你可以将域转移到其他注册机构。

2. **配置允许 Microsoft 365 服务使用域名的 DNS 记录。** 最简单的方法是在步骤3中将域链接到你的 Microsoft 365 订阅时，让向导为你配置 DNS 记录。 如果你想亲自完成此操作，请参阅 [如何为 Microsoft 365 集成手动配置 DNS 记录](#BKMK_ManuallyConfigureDNS)。

3. **将自定义 Internet 域链接到 Microsoft 365 订阅。** 你将使用 "将 **域链接到 Microsoft 365** " 操作。

4. **验证 Microsoft 365 服务是否正在使用新域名。**

   如果在使用 "将 **域链接到 Microsoft 365** 任务" 之前完成了步骤1和步骤2，则向导可以将域名链接到 Microsoft 365。 或者，你可以借助向导完成步骤 1 和步骤 2 的部分或全部操作。

##### <a name="to-link-your-organizations-internet-domain-to-microsoft-365"></a>将组织的 Internet 域链接到 Microsoft 365

1.  在仪表板上，打开 " **Microsoft 365** " 页，然后单击 " **将域链接到 Microsoft 365**"。

2.  按照说明完成向导。

     此向导可帮助你执行注册、配置和链接要在 Microsoft 365 中使用的新的或现有 Internet 域名的部分或全部步骤。

     在向导页上单击帮助链接，以获取完成某个任务所需的信息。 或者参阅 [管理 Windows Server Essentials 中的远程 Web 访问](https://technet.microsoft.com/library/jj628152\(d=printer\).aspx) 的 "设置域名" 部分，了解过程概述和要求。

    > [!NOTE]
    >  若要使用该向导注册新的域名，则必须使用一个与 Microsoft 合作的域名服务提供商，以提供与该向导的无缝集成。 若要查找域名注册机构，请参阅 [如何购买域名](https://office.microsoft.com/office365-suite-help/how-to-buy-a-domain-name-HA102819883.aspx?CTT=5&origin=HA102818660)。

3.  如果向导检测到你的域名未由服务器托管，你将需要手动配置所需的 DNS 记录以完成配置。 有关说明，请参阅本主题后面的 [如何为 Microsoft 365 集成手动配置 DNS 记录](#BKMK_ManuallyConfigureDNS)。

4.  验证域是否正在 Microsoft 365 中使用。

     向导完成后需要等待一些等待，而域名注册机构将验证 DNS 记录。 这会自动发生;无需执行任何操作。 但它通常要花费大约一小时的时间，有时稍长一些。 域验证完成后，" **Microsoft 365** " 页将列出你的组织的域。

####  <a name="how-to-manually-configure-dns-records-for-microsoft-365-integration"></a><a name="BKMK_ManuallyConfigureDNS"></a> 如何为 Microsoft 365 集成手动配置 DNS 记录
 如果 "将域链接到 Microsoft 365 向导" 检测到你的域名未由服务器托管，若要完成配置，必须手动配置所需的域名服务器 (DNS) 记录。 在这种情况下，你会看到一个 DNS 记录列表，你必须在 **% username% \ NewDNSRecords_ (n) .txt**，其中 * (n) * 是一个随机数。

 下表说明了必须添加的 DNS 记录。 输入方法可能因不同的域名注册机构而有所不同。 如果有任何疑问，请向你的域名称注册机构寻求帮助。

### <a name="required-dns-records-for-linking-a-custom-internet-domain-name-to-microsoft-365"></a>将自定义 Internet 域名链接到 Microsoft 365 所需的 DNS 记录

|服务|所需的 DNS 记录|目的|
|-------------|--------------------------|-------------|
|（多个服务）|MX| Microsoft 365 使用此记录来验证你是否拥有特定的域名。 此 MX 记录不会干扰电子邮件路由。|
|Exchange Online|MX|提供电子邮件路由。 **重要提示：**  如果要迁移电子邮件，请不要将 0 (**0**) 的首选项分配给新的 MX 记录。 请确保该记录的值大于分配给当前 MX 记录的值。 当电子邮件迁移完成，并且你已准备好将电子邮件服务器更改为 Microsoft 365 时，请让你的域名注册机构重置新 MX 记录的首选项值。|
|Exchange Online|别名 (CNAME)|自动发现用于帮助用户在 Exchange Online 及其 Outlook 桌面客户端或移动电子邮件客户端之间轻松地设置连接的记录。 **注意：**  如果你想要使用组织自己的域名访问 Outlook Web 访问 (例如 http://mail.contoso.com) (， https://outlook.com/owa/office365.com) 你可以将别名配置为 (cname) 记录，如下所示： **Type = cname，TTL = 01：00：00，HostName = mail，Address = office365**|
|Exchange Online|TXT|指定 outlook.com （Microsoft 365 电子邮件服务器使用的域）有权代表你的域发送电子邮件。 创建此记录，以帮助防止你的出站电子邮件被标记为垃圾邮件。|
|Lync Online|SRV|帮助启用与其他即时消息服务（例如 Windows Live 或 yahoo!）的联盟。|
|Lync Online|SRV|自动发现用于帮助用户在 Lync 桌面客户端和 Microsoft Lync Online 之间轻松地设置连接的记录。|

> [!IMPORTANT]
>  域验证完成后，请不要尝试在 Microsoft 365 门户中添加或对 DNS 记录进行任何进一步的更改。

###  <a name="next-step"></a><a name="BKMK_StepFour_ACCOUNTS"></a> 下一步

-   为用户创建 Microsoft Online Services 帐户。

     若要使用 Microsoft 365 服务，用户必须具有与其网络用户帐户关联的 Microsoft Online Services 帐户。 仪表板使此操作变得简单。 如果使用新的 Microsoft 365 订阅，则可以为现有用户帐户批量创建联机帐户。 如果要将新服务器与已在使用的 Microsoft 365 订阅集成，则可以从现有的联机帐户导入用户帐户。 有关过程，请参阅 [管理用户的联机帐户](Manage-Online-Accounts-for-Users.md)。

> [!NOTE]
>  在 Windows Server Essentials 中的仪表板上，Microsoft Online Services 帐户称为 Microsoft 365 帐户。 这两个帐户是相同的；只有术语发生了更改。

##  <a name="manage-microsoft-365-integration"></a><a name="BKMK_ManageIntegration"></a> 管理 Microsoft 365 集成
 将服务器与 Microsoft 365 集成之后，仪表板上的 **Microsoft 365** 页面将显示有关你的 Microsoft 365 订阅的信息，并使以下任务可用：

-   [管理你的 Microsoft 365 订阅](#BKMK_ManageO365) ？更改用于管理订阅的管理员帐户。 打开 Microsoft 365 管理仪表板以管理你的订阅。

-   [将组织的 Internet 域链接到 Microsoft 365](#BKMK_StepThree) ？如果你希望能够发送和接收发送到你自己的域的电子邮件，则可以将该域链接到 Microsoft 365。 前面所述的 (，请 [参见步骤3：将组织的域链接到 Microsoft 365](#BKMK_StepThree)。 ) 

-   [禁用 Microsoft 365 集成](#BKMK_Disable) ？如果你不想从仪表板管理你的 Microsoft 365 服务、订阅和联机帐户，则可以禁用 Microsoft 365 集成。 在 Microsoft 365 门户上，这些服务仍然可用。

###  <a name="manage-your-microsoft-365-subscription"></a><a name="BKMK_ManageO365"></a> 管理你的 Microsoft 365 订阅
 如果在服务器上工作时需要对 Microsoft 365 订阅进行更改，则可以从仪表板的 " **Microsoft 365** " 页上的 Microsoft 365 中打开订阅。 你还可以更改服务器用于对 Microsoft 365 服务进行更改的管理员帐户。

##### <a name="to-open-your-subscription-on-the-microsoft-365-admin-dashboard"></a>在 Microsoft 365 管理仪表板上打开订阅

1.  在 Windows Server Essentials 仪表板上，打开 " **Microsoft 365** " 页。

2.  在 " **配置任务**" 中，单击 " **管理 Microsoft 365**"。

3.  使用用于管理订阅的 Microsoft 联机帐户登录到 Microsoft 365。

     此时将打开 Microsoft 365 管理仪表板。

##### <a name="to-change-the-microsoft-365-administrator-account"></a>更改 Microsoft 365 管理员帐户

1.  在仪表板上，单击 " **Microsoft 365**"。

2.  在 " **配置任务**" 中，单击 **"更改 Microsoft 365 管理员帐户**。 将出现“更改管理员帐户”向导。  (在 Windows Server Essentials 中，该向导名为 "设置 Microsoft 365 管理员帐户"。 ) 

3.  键入要用于连接到 Microsoft 365 订阅的帐户的凭据，然后单击 " **下一步**"。

4.  单击“关闭” 。 仪表板将重新启动。

###  <a name="disable-microsoft-365-integration"></a><a name="BKMK_Disable"></a> 禁用 Microsoft 365 集成
 如果你决定不想从仪表板管理 Microsoft 365 服务和联机帐户，则可以禁用 Microsoft 365 集成。 你的 Microsoft 365 订阅将保持活动状态，并且在仪表板中所做的任何配置更改都将保持有效。 例如，你将收到电子邮件，该电子邮件将发送到你链接到 Microsoft 365 订阅的域名。 你不会丢失任何电子邮件，并且你为移动设备设置的控件仍使用 Exchange Online。

 今后，你将管理 Microsoft 365 中的 Microsoft 365 订阅、服务和资源，你的用户将需要在 Microsoft 365 中管理其联机帐户的密码。 密码同步不再发生，并且禁用或删除用户帐户将不会对用户的联机帐户产生任何影响。

 因为 Microsoft 365 集成软件安装在本地服务器上，所以即使集成服务无法连接到 Microsoft 365，也可以禁用该功能。

##### <a name="to-disable-microsoft-365-integration-with-the-server"></a>禁用 Microsoft 365 与服务器集成

1.  在仪表板上，单击 " **Microsoft 365**"。

2.  单击 " **禁用 Microsoft 365 集成**"。 此时将显示 "禁用 Microsoft 365 向导"。

3.  按照说明完成向导。

> [!NOTE]
>  若要再次启用 Microsoft 365 集成，请使用仪表板**主页**的 "**服务**" 选项卡上的 "**与 Microsoft 365 集成**" 任务。 有关说明，请参阅本主题前面的 [步骤2：将 Windows Server Essentials 服务器与 Microsoft 365 集成](#BKMK_StepTwo)。

##  <a name="troubleshoot-microsoft-365-integration"></a><a name="BKMK_Troubleshoot"></a> Microsoft 365 集成故障排除
 本部分提供的信息可帮助你解决使用 Windows Server Essentials 中的 Microsoft 365 集成功能时可能遇到的常见问题。

###  <a name="some-microsoft-online-services-accounts-were-not-created"></a><a name="BKMK_AcctsNotCreated"></a> 未创建某些 Microsoft Online Services 帐户
 **说明**

 尝试从仪表板创建一个或多个 Microsoft Online Services 帐户的尝试未成功。

 **解决方案**

1.  单击向导完成页上的链接以打开结果文件，该文件包含未成功完成的每个帐户创建请求的详细信息。 例如，某条结果可能会告诉你，具有请求的帐户名称的 Microsoft Online Services 帐户已存在。

2.  请执行推荐的操作来解决每个错误。

3.  如果此问题仍然存在，请重新启动服务器，然后尝试重新创建联机帐户。

###  <a name="there-was-a-problem-uninstalling-microsoft-365-integration"></a><a name="BKMK_ProblemUninstalling"></a> 卸载 Microsoft 365 集成时出现问题
 **说明**

 尝试禁用 Microsoft 365 集成时出现未知错误。

 **解决方案**

1.  确保计算机已连接到 Internet，然后重试。

2.  如果再次发生该错误，请重新启动服务器，然后重试。

## <a name="additional-references"></a>其他参考

-   [Windows Server Essentials 的服务集成概述-第1部分](/archive/blogs/sbs/services-integration-overview-for-windows-server-2012-r2-essentials-part-1)

-   [Windows Server Essentials 的服务集成概述-第2部分](/archive/blogs/sbs/services-integration-overview-for-windows-server-2012-r2-essentials-part-2)

-   [使用 Microsoft 365 快速入门指南](../use/Quick-Start-Guide-to-Using-Microsoft-Office-365-with-Windows-Server-Essentials.md)

-   [管理 Microsoft Online Services](../manage/Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)

-   [管理 Windows Server Essentials](../manage/Manage-Windows-Server-Essentials.md)