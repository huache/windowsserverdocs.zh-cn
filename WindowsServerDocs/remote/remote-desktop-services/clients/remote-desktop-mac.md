---
title: macOS 客户端入门
description: 了解如何为 Mac 设置远程桌面客户端
ms.topic: article
ms.assetid: 7afc65f8-3158-49c9-9d48-4dab1c69afba
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/20/2020
ms.localizationpriority: medium
ms.openlocfilehash: c7d05731997aeb9fcdb1fadb73ba80f2ff6655e5
ms.sourcegitcommit: 5344adcf9c0462561a4f9d47d80afc1d095a5b13
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90766690"
---
# <a name="get-started-with-the-macos-client"></a>macOS 客户端入门

>适用于：Windows 10、Windows 8.1、Windows Server 2012 R2、Windows Server 2016

可以使用适用于 Mac 的远程桌面客户端从 Mac 计算机处理 Windows 应用、资源和桌面。 使用以下信息可开始使用 - 如果有问题，请查看[常见问题解答](remote-desktop-client-faq.md)。

>[!NOTE]
> - 想知道 macOS 客户端的新版本吗？ 请查看[Mac 上的远程桌面的新增功能有哪些？](mac-whatsnew.md)
> - Mac 客户端在运行 macOS 10.10 及更高版本的计算机上运行。
> - 本文中的信息主要适用于完整版的 Mac 客户端（Mac AppStore 中可用的版本）。 可通过在以下位置下载我们的预览应用来体验新功能：[beta 版客户端发行说明](https://go.microsoft.com/fwlink/?LinkID=619698&clcid=0x409)。

## <a name="get-the-remote-desktop-client"></a>获取远程桌面客户端

按照以下步骤开始在 Mac 上使用远程桌面：

1. 从 [Mac App Store](https://itunes.apple.com/app/microsoft-remote-desktop/id1295203466?mt=12) 下载 Microsoft 远程桌面客户端。
2. [设置电脑接受远程连接](remote-desktop-client-faq.md#how-do-i-set-up-a-pc-for-remote-desktop)。 （如果跳过此步骤中，则无法连接到电脑。）
3. 添加远程桌面连接或远程资源。 可以使用连接直接连接到 Windows 电脑和远程资源，以使用 RemoteApp 程序、基于会话的桌面或是使用 RemoteApp 和桌面连接在本地发布的虚拟桌面。 此功能通常在企业环境中可用。

## <a name="what-about-the-mac-beta-client"></a>Mac beta 版客户端怎么样？

我们要在 AppCenter 上测试预览频道中的新功能。 要看看么？ 转到[适用于 Mac 的 Microsoft 远程桌面](https://aka.ms/rdmacbeta)，然后选择“下载”。 无需创建帐户或登录 AppCenter 即可下载 beta 版客户端。

如果已有该客户端，则可以检查更新，以确保具有最新版本。 在 beta 版客户端中，选择顶部的“Microsoft 远程桌面 Beta”，然后选择“检查是否有更新”。

## <a name="add-a-workspace"></a>添加工作区

订阅管理员提供给你的源，以获取能够在 macOS 设备上访问的受管理资源的列表。

若要订阅源，请执行以下操作：

1. 选择主页上的“添加源”，以连接到服务，并检索资源。
2. 输入源 URL。 该项可以是 URL 或电子邮件地址：
   - 此 URL 通常是一个 Windows 虚拟桌面 URL。 使用哪一个取决于所使用的 Windows 虚拟桌面版本。
      - 对于 Windows 虚拟桌面（经典），请使用 `https://rdweb.wvd.microsoft.com/api/feeddiscovery/webfeeddiscovery.aspx`。
      - 对于 Windows 虚拟桌面，请使用 `https://rdweb.wvd.microsoft.com/api/arm/feeddiscovery`。
   - 若要使用电子邮件地址，请输入你的电子邮件地址。 这会指示客户端搜索与你的电子邮件地址关联的 URL，前提是管理员已采用这种方式配置了服务器。
3. 选择“订阅”。
4. 出现提示时，请使用用户帐户登录。

登录后，应该会看到可用资源的列表。

订阅源后，源的内容会定期自动更新。 资源可能会根据管理员所做的更改而进行添加、更改或删除。

### <a name="export-and-import-connections"></a>导出和导入连接

可以导出远程桌面连接定义并在另一个设备上使用它。 远程桌面保存在单独的 RDP 文件中。

导出 RDP 文件：

1. 在连接中心中，右键单击远程桌面。
2. 选择“导出”。
3. 浏览到要用于保存远程桌面 RDP 文件的位置。
4. 选择“确定”。

导入 RDP 文件：

1. 在菜单栏中，依次选择“文件” > “导入”。
2. 浏览到 RDP 文件。
3. 选择“打开”。

## <a name="add-a-remote-resource"></a>添加远程资源

远程资源包括 RemoteApp 程序、基于会话的桌面和使用 RemoteApp 和桌面连接发布的虚拟桌面。

- URL 会显示指向使你可以访问 RemoteApp 和桌面连接的 RD Web 访问服务器的链接。
- 配置的 RemoteApp 和桌面连接会列出。

若要添加远程资源：

1. 在 Connection Center 中，依次选择“+”和“添加远程资源”。
2. 输入远程资源信息：
   - **源 URL** - RD Web 访问服务器的 URL。 也可以在此字段输入公司电子邮件帐户 - 这将告知客户端搜索与电子邮件地址关联的 RD Web 访问服务器。
   - **用户名称** - 要用于连接到的 RD Web 访问服务器的用户名。
   - **密码** - 要用于连接到的 RD Web 访问服务器的密码。
3. 选择“保存”。

将在“连接中心”显示远程资源。

## <a name="connect-to-an-rd-gateway-to-access-internal-assets"></a>连接到 RD 网关以访问内部资产

远程桌面网关（RD 网关）允许你从 Internet 上的任何位置连接到企业网络上的远程计算机。 可以在应用的首选项中或是在设置新桌面连接期间创建和管理网关。

若要在首选项中设置新网关：

1. 在 Connection Center 中，依次选择“首选项”>“网关”。
2. 选择表底部的“+”按钮，然后输入以下信息：
   - **服务器名称** – 要用作网关的计算机的名称。 可以是 Windows 计算机名、Internet 域名或 IP 地址。 此外可以向服务器名称添加端口信息（例如：RDGateway:443 或 10.0.0.1:443）。
   - **用户名** - 要用于连接到的远程桌面网关的用户名和密码。 还可以选择“使用连接凭据”以使用与用于远程桌面连接的凭据相同的用户名和密码。

## <a name="manage-your-user-accounts"></a>管理用户帐户

当连接到桌面或远程资源时，可以保存用户帐户以便再次选择。 可以使用远程桌面客户端管理用户帐户。

若要创建新的用户帐户：

1. 在 Connection Center 中，依次选择“设置” > “帐户”。
2. 选择“添加用户帐户”。
3. 输入以下信息：
   - **用户名** - 要保存以用于远程连接的用户名。 可以使用以下任意格式输入用户名：user_name、domain\user_name 或 user_name@domain.com。
   - **密码** - 指定的用户密码。 要保存用于远程连接的每个用户帐户都需要与之关联的密码。
   - 友好名称 - 如果使用具有不同密码的相同用户帐户，则设置友好名称以区分这些用户帐户。
4. 依次选择“保存”和“设置”。

## <a name="customize-your-display-resolution"></a>自定义显示分辨率

可以为远程桌面会话指定显示分辨率。

1. 在 Connection Center 中，选择“首选项”。
2. 选择“分辨率”。
3. 选择“+”。
4. 输入分辨率高度和宽度，然后选择“确定”。

若要删除分辨率，请依次选择要删除的分辨率和“-”。

## <a name="displays-have-separate-spaces"></a>显示具有单独的空间

如果正在运行 Mac OS X 10.9 并且已在 Mavericks 中禁用“显示具有单独的空间”（“系统首选项”>“任务控制”），则需要使用相同选项在远程桌面客户端中配置此设置 。

### <a name="drive-redirection-for-remote-resources"></a>远程资源的驱动器重定向

远程资源支持驱动器重定向，以便可以将使用远程应用程序创建的文件在本地保存到 Mac。 重定向的文件夹始终是在远程会话中显示为网络驱动器的主目录。

> [!NOTE]
> 若要使用此功能，管理员需要在服务器上设置适当的设置。

## <a name="use-a-keyboard-in-a-remote-session"></a>在远程会话中使用键盘

Mac 键盘布局与 Windows 键盘布局不同。

- Mac 键盘上的 Command 键等于 Windows 键。
- 若要执行使用 Mac 上的 Command 按钮的操作，则需要使用 Windows 中的控制按钮（例如：Copy = Ctrl+C）。
- 可以通过额外按 FN 键在会话中激活功能键（例如：FN+F1）。
- Mac 键盘上空格键右侧的 Alt 键等于 Windows 中的 Alt Gr/右 Alt 键。

默认情况下，远程会话会使用与客户端运行的操作系统相同的键盘区域设置。 （如果 Mac 运行美国英语操作系统，则也会对远程会话使用该操作系统。）如果未使用操作系统键盘区域设置，请检查远程电脑上的键盘设置并手动更改该设置。 有关键盘和区域设置的更多信息，请参阅[远程桌面客户端常见问题解答](remote-desktop-client-faq.md)。

## <a name="support-for-remote-desktop-gateway-pluggable-authentication-and-authorization"></a>对远程桌面网关可插入身份验证和授权的支持

Windows Server 2012 R2 引入了对新身份验证方法（即远程桌面网关可插入身份验证和授权）的支持，该方法可为自定义身份验证例程提供更高的灵活性。 现在可以通过 Mac 客户端尝试此身份验证模型。

> [!IMPORTANT]
> 不支持 Windows 8.1 之前的自定义身份验证和授权模型，尽管上面的文章讨论了它们。

若要了解有关此功能的更多信息，请查看 [https://aka.ms/paa-sample](/samples/browse/?redirectedfrom=MSDN-samples)。

> [!TIP]
> 欢迎提出问题和意见。 但是，请不要使用本文末尾的评论功能来请求获取故障排除帮助。 而是转到[远程桌面客户端论坛](/answers/topics/windows-remote-desktop-client.html)并启动一个新线程。 有功能建议？ 请在[客户端用户心声论坛](https://remotedesktop.uservoice.com/forums/272085-remote-desktop-for-android)告诉我们。