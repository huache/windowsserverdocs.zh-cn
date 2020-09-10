---
title: 更改媒体流设置
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: dec690d2-f80c-4b09-99d6-3bba41331972
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 041a7f53b02d9b6b6368bd2b2f4ac991a14a61fa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623879"
---
# <a name="change-media-streaming-settings"></a>更改媒体流设置

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

你可以使用多个选项来更改媒体流设置。 提供了以下选项：

-   [隐藏远程媒体流加载项](Change-Media-Streaming-Settings.md#BKMK_DisableRemote)

-   [设置媒体库名称](Change-Media-Streaming-Settings.md#BKMK_LibraryName)

-   [设置视频流质量](Change-Media-Streaming-Settings.md#BKMK_StreamingQuality)

-   [以编程方式启用或禁用媒体流](Change-Media-Streaming-Settings.md#BKMK_Program)

##  <a name="hide-remote-media-streaming-add-in"></a><a name="BKMK_DisableRemote"></a> 隐藏远程媒体流加载项
 你可以通过在注册表中添加项来隐藏远程媒体流加载项。

#### <a name="to-hide-the-remote-media-streaming-add-in"></a>隐藏远程媒体流加载项

1.  在服务器上，将鼠标移动到屏幕右上角，然后单击 **“搜索”**。

2.  在 **“搜索”** 框中，键入 **regedit**，然后单击 **“Regedit”** 应用程序。

3.  在左侧窗格中，向下展开到以下注册表项：

     **“HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\RemoteAccess\DisabledAddIns”**

4.  右键单击 **“DisabledAddIns”**，指向 **“新建”**，然后单击 **“DWORD 值”**。

5.  在新值中输入 **497796c6-9cc7-43be-aa26-4e6b5695370d**，该值为远程媒体流加载项的标识符，然后按 **Enter**。

6.  右键单击该值，然后单击 **“修改”**。

7.  输入 **1** 作为值数据，然后单击 **“确定”**。

##  <a name="set-the-media-library-name"></a><a name="BKMK_LibraryName"></a> 设置媒体库名称
 你可以使用 Windows Server 解决方案 SDK 中的某个类来设置媒体库的名称。 若要设置媒体库的名称，你可以使用 **Microsoft.WindowsServerSolutions.MediaStreaming** 命名空间中 **MediaStreamingManager** 类的 **SetMediaLibraryName** 方法。 以下示例显示了如何设置媒体库的名称：

```c#

MediaStreamingManager mediaStreamingManager = new MediaStreamingManager();
string mediaLibraryName = Guid.NewGuid().ToString("B");
mediaStreamingManager.SetMediaLibraryName(mediaLibraryName);

```

 有关详细信息，请参阅 [Windows Server Solutions SDK](https://go.microsoft.com/fwlink/?LinkID=248648)（Windows Server 解决方案 SDK）。

##  <a name="set-video-streaming-quality"></a><a name="BKMK_StreamingQuality"></a> 设置视频流质量
 你可以通过获取 WinSAT CPU 分数，然后创建和安装包含 WinSAT 分数信息的 .xml 文件来设置视频流质量。 如果在初始配置运行之前安装了包含 WinSAT 分数信息的 .xml 文件，则不会向客户显示设置视频质量的用户界面。 有关详细信息，请参阅[在服务器上设置 WinSAT 分数](Set-the-WinSAT-Score-on-the-Server.md)。

##  <a name="programmatically-enable-or-disable-media-streaming"></a><a name="BKMK_Program"></a> 以编程方式启用或禁用媒体流
 你可以使用 Windows Server 解决方案 SDK 中的某个类以编程方式启用或禁用媒体流。 若要启用或禁用媒体流，你可以使用 **Microsoft.WindowsServerSolutions.MediaStreaming** 命名空间中 **MediaStreamingManager** 类的 **SetMediaStreamingEnabled** 方法。 下面的代码示例显示了如何启用媒体流：

```c#

MediaStreamingManager mediaStreamingManager = new MediaStreamingManager();
mediaStreamingManager.SetMediaStreamingEnabled(true);

```

 下面的代码示例显示了如何禁用媒体流：

```c#

MediaStreamingManager mediaStreamingManager = new MediaStreamingManager();
mediaStreamingManager.SetMediaStreamingEnabled(false);
```

## <a name="see-also"></a>另请参阅
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)