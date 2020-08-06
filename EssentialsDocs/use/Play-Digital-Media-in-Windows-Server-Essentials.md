---
title: 在 Windows Server Essentials 中播放数字媒体
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 5f570492-ee21-471b-92c1-3fd9bfb84f55
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 1ce7359929cb1658cc84418231fb7d65efce8692
ms.sourcegitcommit: 04637054de2bfbac66b9c78bad7bf3e7bae5ffb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87838216"
---
# <a name="play-digital-media-in-windows-server-essentials"></a>在 Windows Server Essentials 中播放数字媒体

>适用于： Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

数字媒体是指已被数字压缩的音频、视频和照片内容。  Windows Server Essentials 使联网的计算机和某些联网数字媒体设备可以播放存储在服务器上的数字媒体文件。

 以下主题提供有关访问和播放存储在 Windows Server Essentials 上的数字媒体文件的信息：


-   [数字媒体概述](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_1)

-   [播放和共享数字媒体](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2)

-   [从远程位置播放共享的数字媒体文件](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_3)

-   [将数字媒体文件添加到服务器](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_4)

-   [下载格式选项](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_5)

-   [轻松文件上载工具](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_6)

-   [查看和浏览共享的数字媒体](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_7)


##  <a name="digital-media-overview"></a><a name="BKMK_1"></a>数字媒体概述
 数字媒体是指已编码（数字压缩）的音频、视频和照片内容。 编码内容包括将音频和视频输入转换为数字媒体文件，如 Windows Media 文件。 对数字媒体进行编码后，它可以通过计算机方便地操作、分发和播放，并且轻松地通过计算机网络传输。

 数字媒体类型的示例包括：Windows Media 音频 (WMA)、Windows Media 视频 (WMV)、MP3、JPEG　和 AVI。 有关 Windows Media Player 支持的数字媒体类型的信息，请参阅 [Windows Media Player 支持的文件类型](https://support.microsoft.com/kb/316992)。

### <a name="why-would-i-want-to-stream-my-digital-media"></a>为何要流式传输数字媒体？
 许多人将音乐、视频和图片存储在 Windows Server Essentials 的共享文件夹中。 可能有些时候你想要执行以下操作：

-   **观看视频**。 你的服务器可用于存储视频的大集合和录制的电视节目以及将它们流式传输到你的计算机或网络上的其他播放设备。 通过使用 Windows Media Player，可以将视频流媒体传送到 Xbox 360 或计算机。

-   **播放音乐**。 当你打开 **“音乐”** 共享文件夹的媒体共享时，可以从支持 Windows Media Connect 的设备访问你的音乐。 打开共享后，不需要从 **“音乐”** 共享文件夹中启用或配置任何用户帐户以进行流式传输。

-   **显示照片幻灯片**。 可以将你的数字照片存储在服务器上的 **“照片”** 共享文件夹中，然后从任何计算机或连接到你家庭或办公室中的电视的 Xbox 360 访问它们。 可以观看照片幻灯片，就像将你的电视变成大相框一样。

### <a name="sharing-copy-protected-media"></a>共享受版权保护的媒体
  Windows Server Essentials 不支持共享受版权保护的媒体。 这包括通过在线音乐商店购买的音乐。

 仅可以在用于购买它的计算机或设备上播放受版权保护的媒体。 版权保护防止你在多个计算机或设备上播放媒体，即使你将媒体复制到服务器并从那里播放它。 但是，可以在 Windows Server Essentials 上存储受版权保护的媒体，并继续在用来购买它的计算机或设备上播放该媒体。

##  <a name="play-and-share-digital-media"></a><a name="BKMK_2"></a>播放和共享数字媒体
 设置网络并将计算机和媒体设备成功连接到服务器网络后，你可以搜索你在服务器上存储和共享的任何数字媒体文件。

> [!NOTE]
>  有关与 Windows Server Essentials 兼容的数字媒体播放器/接收设备的当前列表，请参阅[Windows 兼容性中心](https://www.microsoft.com/windows/compatibility/CompatCenter/Home)。

 你可以使用以下任一方法来搜索和播放存储在你的服务器上的数字媒体文件：

-   [从网络上的计算机或数字媒体播放器搜索和播放 Windows Server Essentials 上的媒体文件](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2.1)

-   [将 Windows Server Essentials 上的媒体文件发送到 Windows Media Player、Xbox 360，或发送到网络中的联网数字媒体播放器](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_SendToDevice)


###  <a name="search-for-and-play-media-files-on-windows-server-essentials-from-a-computer-or-digital-media-player-on-the-network"></a><a name="BKMK_2.1"></a>从网络上的计算机或数字媒体播放器搜索和播放 Windows Server Essentials 上的媒体文件
 当你的设备加入到 Windows Server Essentials 网络时，你可以通过以下任一方式搜索和播放数字媒体文件：


-   [从运行 Windows Media Center 的计算机上搜索和播放媒体文件](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_WMC)

-   [通过使用 Windows Media Player 从运行 Windows 的计算机搜索和播放媒体文件](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_MWP)

-   [通过使用 Xbox 360 搜索和播放媒体文件](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_Xbox)

-   [使用与 Windows Server Essentials 兼容的其他数字媒体播放器或接收器搜索和播放媒体文件](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_Other)

-   [通过使用快速启动板的共享文件夹功能搜索和播放媒体文件](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_SharedFolders)

-   [通过使用远程 Web 访问搜索和播放共享的媒体](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_RWA2)


####  <a name="search-for-and-play-media-files-from-a-computer-that-is-running-windows-media-center"></a><a name="BKMK_WMC"></a>在运行 Windows Media Center 的计算机上搜索和播放媒体文件

1.  依次单击 **“开始”**、**“所有程序”** 和 **“Windows Media Center”**。

2.  在 **“Windows Media Center”** 页上，滚动到你要搜索的媒体类型，并单击该媒体库。

3.  手动搜索你感兴趣的文件，或单击 **“搜索”** 并键入你要查找的文件的名称。

4.  单击媒体文件映像以查看或播放该文件。

####  <a name="search-for-and-play-media-files-from-a-computer-that-is-running-windows-by-using-windows-media-player"></a><a name="BKMK_MWP"></a>使用 Windows Media Player 从运行 Windows 的计算机搜索和播放媒体文件

-   从计算机或媒体设备中，打开 **“Windows Media Player”** 并搜索你的媒体库。

    > [!NOTE]
    >  搜索步骤因你使用的 Windows Media Player 的版本而异。 有关详细信息，请参考你的版本的帮助。

####  <a name="search-for-and-play-media-files-by-using-xbox-360"></a><a name="BKMK_Xbox"></a>使用 Xbox 360 搜索和播放媒体文件

1.  通过使用有线或无线连接将 Xbox 360 控制台连接到你的家庭网络。

2.  在运行 Windows Server Essentials 的计算机上，打开 "媒体共享"。 有关详细信息，请参阅[打开或关闭媒体流](../manage/Manage-Digital-Media-in-Windows-Server-Essentials.md#BKMK_4)主题。

3.  若要使用 Xbox 360 控制台播放数字媒体文件：

    1.  转到 **“My Xbox”**，然后选择 **“视频库”**、**“音乐库”** 或 **“图片库”**，具体取决于你想要查看或播放的媒体类型。

    2.  选择你的服务器的名称。

        > [!NOTE]
        >  如果未列出你的服务器的名称，则选择 **“计算机”**，然后单击 **“测试连接”**。

    3.  浏览文件列表并选择要播放的项。

####  <a name="search-for-and-play-media-files-by-using-other-digital-media-players-or-receivers-that-are-compatible-with-windows-server-essentials"></a><a name="BKMK_Other"></a>使用与 Windows Server Essentials 兼容的其他数字媒体播放器或接收器搜索和播放媒体文件

1.  转到 [Windows 兼容性中心](https://www.microsoft.com/windows/compatibility/CompatCenter/Home) 并确保你的数字媒体播放器或接收器在兼容设备的列表中显示。

2.  由于搜索的步骤根据你正在使用的数字媒体播放器而有所不同，因此请参考你的设备的帮助以获取详细说明。

####  <a name="search-for-and-play-media-files-by-using-the-shared-folders-feature-of-the-launchpad"></a><a name="BKMK_SharedFolders"></a>使用快速启动板的共享文件夹功能搜索和播放媒体文件

1.  登录到 Windows Server Essentials 快速启动板。

2.  从快速启动板中单击 **“共享文件夹”**。 Windows 资源管理器窗口打开，并显示服务器上的共享文件夹。

3.  在 **“搜索”** 框中，键入媒体文件的名称。 显示搜索查询的结果。

    > [!NOTE]
    >  作为一个选项，你还可以双击共享文件夹，以浏览文件夹内容。

####  <a name="search-for-and-play-shared-media-by-using-remote-web-access"></a><a name="BKMK_RWA2"></a>使用远程 Web 访问搜索和播放共享的媒体

1.  登录到远程 Web 访问。

2.  单击“共享文件夹”。 Web 页面的 **“共享文件夹”** 部分在服务器上的共享文件夹的列表中显示。

3.  双击一个文件夹以查看该文件夹的内容。

###  <a name="send-media-files-on-windows-server-essentials-to-windows-media-player-xbox-360-or-to-a-networked-digital-media-player-in-the-network"></a><a name="BKMK_SendToDevice"></a>将 Windows Server Essentials 上的媒体文件发送到 Windows Media Player、Xbox 360，或发送到网络中的联网数字媒体播放器
 使用 **“Windows Media Player”** 搜索你要的媒体文件。 右键单击此媒体文件，然后单击 **“播放到”** 以将此媒体文件发送到联网的媒体设备。

##  <a name="play-shared-digital-media-files-from-a-remote-location"></a><a name="BKMK_3"></a>从远程位置播放共享的数字媒体文件
 使用远程 Web 访问离开 Windows Server Essentials 网络时，可以播放媒体文件。 可以使用移动电话、远程计算机或数字媒体播放器来搜索和播放你存储在服务器上的共享媒体文件。

#### <a name="to-play-shared-media-files-when-you-are-away-from-the-network"></a>当你离开网络时播放共享的媒体文件

1. 打开 Internet 浏览器。

2. 转到远程 Web 访问网站。 在 Internet 浏览器的地址栏中键入**https://<YourDomainName \> /remote** ，然后按 enter。

   > [!NOTE]
   >  *<YourDomainName \> *是占位符。 它将是服务器独有的名称，因此键入的地址将类似于 **https://contoso.com/remote** 。 当在服务器上设置远程访问功能时，如果不知道你的域的名称，则请询问选择域名的管理员。 有关详细信息，请参阅[启用远程 Web 访问](../manage/Manage-Remote-Web-Access-in-Windows-Server-Essentials.md#BKMK_TurnOnRWA)。

3. 在远程 Web 访问登录页上，键入你的用户帐户名和密码，然后单击箭头。

4. 使用你喜欢的任意方法搜索要播放的媒体文件。

   > [!NOTE]
   >
   >  有关各种搜索方法的信息，请参阅在[网络上从计算机或数字媒体播放器搜索和播放 Windows Server Essentials 上的媒体文件](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2.1)。
   >
   >  有关各种搜索方法的信息，请参阅在[网络上从计算机或数字媒体播放器搜索和播放 Windows Server Essentials 上的媒体文件](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2.1)。


5. 当媒体文件名称出现时，单击该文件名称以播放媒体。

##  <a name="add-digital-media-files-to-the-server"></a><a name="BKMK_4"></a>将数字媒体文件添加到服务器

 服务器管理员可以通过直接访问服务器或通过使用远程 Web 访问站点登录到仪表板，将数字媒体添加到媒体库中的共享文件夹。 其他用户可以通过使用 "快速启动板" 上的 "**共享文件夹**" 连接、通过使用远程 Web 访问站点或使用适用于 Windows Phone 的 My server 应用，将媒体文件添加到服务器。 有关播放媒体的信息，请参阅[播放和共享数字媒体](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2)。

 服务器管理员可以通过直接访问服务器或通过使用远程 Web 访问站点登录到仪表板，将数字媒体添加到媒体库中的共享文件夹。 其他用户可以通过使用 "快速启动板" 上的 "**共享文件夹**" 连接、通过使用远程 Web 访问站点或使用适用于 Windows Phone 的 My server 应用，将媒体文件添加到服务器。 有关播放媒体的信息，请参阅[播放和共享数字媒体](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2)。


> [!NOTE]
>  通过使用适用于 Windows Phone 的 My Server 应用，还可以将媒体文件上载到服务器。 你可以从 [Windows Phone 应用商店](http://www.windowsphone.com/store/app/my-server/6c2f98d5-6fcf-4e1d-b8b1-cde62ea1a94a)下载 My Server 应用。 有关 "我的服务器" 应用 Windows Phone 的详细信息，请参阅博客文章[适用于 Windows Server Essentials 的 My server](/archive/blogs/sbs/my-server-phone-app-for-windows-server-2012-essentials)应用。

#### <a name="to-add-digital-media-files-to-shared-folders-on-the-server"></a>将数字媒体文件添加到服务器上的共享文件夹

1.  使用以下方法之一登录到服务器：


    1.  有关登录到远程 Web 访问的信息，请参阅[使用远程 Web 访问](Use-Remote-Web-Access-in-Windows-Server-Essentials.md)。

    1.  有关登录到远程 Web 访问的信息，请参阅[使用远程 Web 访问](../use/Use-Remote-Web-Access-in-Windows-Server-Essentials.md)。


    2.  有关通过快速启动板登录的信息，请参阅[快速启动板概述](../manage/Overview-of-the-Launchpad-in-Windows-Server-Essentials.md)。

2.  搜索并单击你要添加的媒体的文件夹。

3.  将要添加的媒体文件复制并粘贴或拖放到服务器上的相应共享文件夹。

##  <a name="download-format-options"></a><a name="BKMK_5"></a>下载格式选项
 有两个下载文件的选项。 仅当你将多个文件或一个文件夹下载到基于 Windows 的计算机时，这些选项才可用。

 选择以下符合你的下载需求的选项：

- **压缩的 ZIP 文件 (.zip)**

   压缩文件能够创建小于原始文件的文件压缩版本。 该压缩版本的文件具有 .zip 文件扩展名。 通过压缩大小能减少的文件类型是面向文本的文件类型（如 .txt、.doc 和 .xls），以及使用非压缩文件类型（如 .bmp）的图形文件。 某些图形文件（如 .jpg 和 .gif 文件）已经使用过压缩，因此通过压缩，文件的大小减小得非常少。 此外，与大部分是文本的文档相比，包含大量图形的 Word 文档无法减少得一样多。

  > [!NOTE]
  >  此选项对国际文件名称提供有限的支持。

- **自解压可执行文件 (.exe)**

   自解压可执行文件是你可以下载的文件，此文件将解压缩（可执行）程序与压缩的文件组合在一起。 当你运行可执行程序时，它会自动解压缩压缩的文件。 这是分发压缩数据的常用方式，无需担心收件人是否具有正确的解压缩实用工具。

  > [!NOTE]
  >  此选项支持 Unicode 字符。

  开始实际下载之前，将创建 exe 或 zip 文件。 这可能需要几分钟，具体取决于文件的数量和要下载文件的总大小。 创建下载文件后，下载文件的操作发生在后台。 这允许你在下载过程完成时可以继续工作。

##  <a name="easy-file-upload-tool"></a><a name="BKMK_6"></a>轻松文件上载工具
 轻松文件上载工具简化了在 Windows Server Essentials 服务器上上传文件的过程。 你可以根据需要将任意多个文件添加到轻松文件上载工具，然后将它们上载到 Windows Server Essentials 服务器上的共享文件夹中。 有关详细信息，请参阅博客文章 [了解远程 Web 访问文件共享](/archive/blogs/sbs/understanding-remote-web-access-file-sharing)。

##  <a name="view-and-browse-shared-digital-media"></a><a name="BKMK_7"></a>查看和浏览共享的数字媒体
 通过使用仪表板、快速启动板、远程 Web 访问网站或适用于 Windows Phone 的 My Server 应用，你可以查看或浏览资源。

#### <a name="to-view-and-browse-shared-media-from-the-dashboard"></a>从仪表板查看和浏览共享的媒体

1.  打开服务器仪表板。

2.  在主导航栏上，单击 **“存储”**。

3.  单击 "**服务器文件夹**" 选项卡。此时将显示服务器文件夹的列表。

4.  双击一个文件夹以查看该文件夹的内容。

#### <a name="to-view-and-browse-shared-media-using-the-launchpad-from-a-network-computer"></a>从网络计算机使用快速启动板查看和浏览共享的媒体

1.  登录到快速启动板。

2.  单击“共享文件夹”。 Windows 资源管理器打开并显示服务器上的共享文件夹的列表。

3.  双击一个文件夹以查看该文件夹的内容。

#### <a name="to-view-and-browse-shared-media-using-remote-web-access"></a>使用远程 Web 访问查看和浏览共享的媒体

1.  登录到远程 Web 访问。

2.  单击“共享文件夹”。 Web 页面的 **“共享文件夹”** 部分在服务器上的共享文件夹的列表中显示。

3.  双击一个文件夹以查看该文件夹的内容。

## <a name="additional-references"></a>其他参考

-   [管理数字媒体](../manage/Manage-Digital-Media-in-Windows-Server-Essentials.md)

-   [连接](Get-Connected-in-Windows-Server-Essentials.md)

-   [使用共享文件夹](Use-Shared-Folders-in-Windows-Server-Essentials.md)

-   [远程工作](Work-Remotely-in-Windows-Server-Essentials.md)