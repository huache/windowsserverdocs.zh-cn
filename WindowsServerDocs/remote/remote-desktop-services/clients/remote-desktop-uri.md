---
title: 远程桌面 URI 方案
description: 了解远程桌面客户端的统一资源标识符方案
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
ms.assetid: 0c3f1eb6-835c-4522-99ff-56c6ee4bb911
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 06/01/2020
ms.localizationpriority: medium
ms.openlocfilehash: 50eb7aaa9b8d4d8826f74f2a5338c93dee5d1053
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86954069"
---
# <a name="remote-desktop-uri-scheme"></a>远程桌面 URI 方案

> 适用于：Windows Server 版本 1803、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2

本文档定义了远程桌面的统一资源标识符 (URI) 的格式。 通过这些 URI 方案，可使用各种命令调用远程桌面客户端。

## <a name="ms-rd-uri-scheme"></a>ms-rd URI 方案

>[!NOTE]
> ms-rd URI 方案当前仅支持用于 Windows 桌面客户端 (MSRDC)。

通过 ms-rd URI，可按以下格式为客户端指定一个命名并指定一组该命令特定的参数：

```
ms-rd:command?parameters
```

参数采用查询字符串格式“键=值对”（用 & 分隔）为给定命令提供额外的信息：

```
param1=value1&param2=value2&…
```

### <a name="commands-and-parameters"></a>命令和参数

下面列表中是当前支持的命令及其相应的参数。

使用不带任何命令的 `ms-rd:` 启动客户端。

#### <a name="subscribe"></a>Subscribe

此命令会启动客户端和订阅过程。

**命令名称：** subscribe

**命令参数：**

| 参数 | 说明                  | 值 |
|-----------|------------------------------|--------|
| url       | 指定工作区 URL。 | 有效的 URL，例如 <https://contoso.com>。 |

**示例：** ms-rd:subscribe?url=https://contoso.com

## <a name="legacy-rdp-uri-scheme"></a>旧的 rdp URI 方案

>[!NOTE]
> 以下 URI 方案仅支持用于 macOS、iOS 和 Android 设备的客户端。 它将被上述新的 ms-rd URI 取代。

Microsoft 远程桌面使用 URI 方案 rdp://query_string 来存储启动客户端时使用的预配置的特性设置。 查询字符串表示 URL 中提供的单个实例或一组 RDP 特性。

RDP 属性用与号 (&) 分隔。 例如，连接到 PC 时，该字符串是：

```
rdp://full%20address=s:mypc:3389&audiomode=i:2&disable%20themes=i:1
```

此表提供可以与 iOS、Mac 和 Android 远程桌面客户端一起使用的受支持特性的完整列表。 （平台列中的“x”指示该特性受支持。 通过尖括号 (<>) 指示的值表示远程桌面客户端支持的值。）

| RDP 特性                                           | Android | Mac | iOS |
|---------------------------------------------------------|---------|-----|-----|
| allow desktop composition=i:&lt;0 或 1&gt;              | x       | x   | x   |
| allow font smoothing=i:<0 或 1&gt;                      | x       | x   | x   |
| alternate shell=s:&lt;字符串&gt;                        | x       | x   | x   |
| [audiomode=i:&lt;0、1 或 2&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393707(v=ws.10)) | x       | x   | x   |
| [authentication level=i:&lt;0 或 1&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393709(v=ws.10)) | x       | x   | x   |
| connect to console=i:&lt;0 或 1&gt;                     | x       | x   | x   |
| disable cursor settings=i:&lt;0 或 1&gt;                | x       | x   | x   |
| disable full window drag=i:&lt;0 或 1&gt;               | x       | x   | x   |
| disable menu anims=i:&lt;0 或 1&gt;                     | x       | x   | x   |
| disable themes=i:&lt;0 或 1&gt;                         | x       | x   | x   |
| disable wallpaper=i:&lt;0 或 1&gt;                      | x       | x   | x   |
| [drivestoredirect=s:*](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393728(v=ws.10)) （这是唯一受支持的值） | x       | x   |     |
| [desktopheight=i:&lt;以像素为单位的值&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393702(v=ws.10)) |         | x   |     |
| [desktopwidth=i:&lt;以像素为单位的值&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393697(v=ws.10))  |         | x   |     |
| [domain=s:&lt;字符串&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393673(v=ws.10))                 | x | x | x |
| [full address=s:&lt;字符串&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393661(v=ws.10))           | x | x | x |
| gatewayhostname=s:&lt;字符串&gt;                  | x | x | x |
| [gatewayusagemethod=i:&lt;1 或 2&gt;](/windows/win32/termserv/imsrdpclienttransportsettings-gatewayusagemethod)                | x | x | x |
| [prompt for credentials on client=i:&lt;0 或 1&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393660(v=ws.10)) |   | x |   |
| [loadbalanceinfo=s:&lt;字符串&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393684(v=ws.10))                  | x | x | x |
| [redirectprinters=i:&lt;0 或 1&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393671(v=ws.10))                 |   | x |   |
| remoteapplicationcmdline=s:&lt;字符串&gt;         | x | x | x |
| remoteapplicationmode=i:&lt;0 或 1&gt;            | x | x | x |
| remoteapplicationprogram=s:&lt;字符串&gt;         | x | x | x |
| shell working directory=s:&lt;字符串&gt;          | x | x | x |
| Use redirection server name=i:&lt;0 或 1&gt;      | x | x | x |
| [username=s:&lt;字符串&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393678(v=ws.10))                  | x | x | x |
| [screen mode id=i:&lt;1 或 2&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393692(v=ws.10))            |   | x |   |
| [session bpp=i:&lt;8、15、16、24 或 32&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393680(v=ws.10)) |   | x |   |
| [use multimon=i:&lt;0 或 1&gt;](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/ff393695(v=ws.10))              |   | x |   |
