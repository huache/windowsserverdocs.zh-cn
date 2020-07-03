---
title: 受支持的远程桌面 RDP 文件设置
description: 了解远程桌面的 RDP 文件设置
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.topic: article
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 06/30/2020
ms.localizationpriority: medium
ms.openlocfilehash: 8132c6d996a3e814b15eb34b713832fb6a98d6a0
ms.sourcegitcommit: 643a9916efb95ad0bb5cc0a9b115ac29af4cb076
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/30/2020
ms.locfileid: "85586699"
---
# <a name="supported-remote-desktop-rdp-file-settings"></a>受支持的远程桌面 RDP 文件设置

下表列出了可用于远程桌面客户端的受支持的 RDP 文件设置。 配置设置时，检查[客户端比较](./remote-desktop-app-compare.md)以查看每个客户端支持的重定向。

此表还突出显示了 Windows 虚拟桌面支持哪些设置作为自定义属性。 可以参阅[这篇文档](/azure/virtual-desktop/customize-rdp-properties/)，详细了解如何使用 PowerShell 为 Windows 虚拟桌面主机池自定义 RDP 属性。

## <a name="connection-information"></a>连接信息

| RDP 设置                        | 说明            | 值                 | 默认值          | Windows 虚拟桌面支持 |
|------------------------------------|------------------------|------------------------|:----------------------:|:-----------------------:|
| full address:s:value | 电脑名称：</br>此设置指定要连接到的远程计算机的名称或 IP 地址。</br></br>这是 RDP 文件中唯一需要的设置。 | 有效的名称、IPv4 地址或 IPv6 地址。 | | 否 |
| alternate full address:s:value | 指定远程计算机的备用名称或 IP 地址。 | 有效的名称、IPv4 地址或 IPv6 地址。 | | 否 |
| username:s:value | 指定用于登录远程计算机的用户帐户的名称。 | 任何有效的用户名。 | | 否 |
| domain:s:value | 指定用于登录远程计算机的用户帐户所在域的名称。 | 有效的域名（如“CONTOSO”）。 | | 否 |
| gatewayhostname:s:value | 指定 RD 网关主机名。 | 有效的名称、IPv4 地址或 IPv6 地址。 | | 否 |
| gatewaycredentialssource:i:value | 指定 RD 网关身份验证方法。 | - 0：要求提供密码 (NTLM)</br>- 1：使用智能卡</br>- 2：使用当前已登录的用户的凭据。</br>- 3：提示用户输入其凭据并使用基本身份验证</br>- 4：允许用户稍后选择</br>- 5：使用基于 Cookie 的身份验证 | 0 | 否 |
| gatewayprofileusagemethod:i:value | 指定是否使用默认 RD 网关设置。 | - 0：使用管理员指定的默认配置文件模式</br>- 1：使用用户指定的显式设置 | 0 | 否 |
| gatewayusagemethod:i:value | 指定何时将 RD 网关用于连接。 | - 0：不使用 RD 网关</br>- 1：始终使用 RD 网关</br>- 2：在无法与 RD 会话主机建立直接连接的情况下使用 RD 网关</br>- 3：使用默认 RD 网关设置</br>- 4：不使用 RD 网关，对本地地址绕过网关</br>将此属性值设置为 0 或 4 实际上是等效的，但将此属性设置为 4 会启用绕过本地地址的选项。 | 0 | 否 |
| promptcredentialonce:i:value | 确定是否保存用户的凭据并将其用于 RD 网关和远程计算机。 | - 0：远程会话不使用相同的凭据</br>- 1：远程会话将使用相同的凭据 | 1 | 否 |
| authentication level:i:value | 定义服务器身份验证级别设置。 | - 0：如果服务器身份验证失败，请在不显示警告的情况下连接到计算机（连接且不向我发出警告）</br>- 1：如果服务器身份验证失败，请不要建立连接（不要连接）</br>- 2：如果服务器身份验证失败，请显示警告并允许我连接或拒绝连接（向我发出警告）</br>- 3：未指定身份验证要求。 | 3 | 否 |
| enablecredsspsupport:i:value | 确定客户端是否会在凭据安全支持提供程序 (CredSSP) 可用的情况下使用它来进行身份验证。 | - 0：即使操作系统支持 CredSSP，RDP 也不会使用 CredSSP</br>- 1：如果操作系统支持 CredSSP，则 RDP 将使用 CredSSP | 1 | 是 |
| disableconnectionsharing:i:value | 确定客户端在新连接启动时是重新连接到任何已断开连接的现有会话，还是启动新连接。 | - 0：重新连接到任何现有会话</br>- 1：启动新的连接 | 0 | 是 |
| alternate shell:s:value | 指定要在远程会话中作为 shell（而不是资源管理器）自动启动的程序。 | 指向可执行文件的有效路径（如“C:\ProgramFiles\Office\word.exe”） | | 是 |

## <a name="session-behavior"></a>会话行为

| RDP 设置                        | 说明            | 值                 | 默认值          | Windows 虚拟桌面支持 |
|------------------------------------|------------------------|------------------------|:----------------------:|:-----------------------:|
| autoreconnection enabled:i:value | 确定客户端是否会在连接断开时（例如，当网络连接中断时）自动尝试重新连接到远程计算机。 | - 0：客户端不自动尝试重新连接</br>- 1：客户端自动尝试重新连接 | 1 | 是 |
| bandwidthautodetect:i:value | 确定是否启用了自动网络类型检测 | - 0：禁用自动网络类型检测</br>- 1：启用自动网络类型检测 | 1 | 是 |
| networkautodetect:i:value | 确定是否使用自动网络带宽检测。 需要将 bandwidthautodetect 设置为 1。 | - 0：不使用自动网络带宽检测</br> - 1：使用自动网络带宽检测 | 1 | 是 |
| compression:i:value | 确定在通过 RDP 传输到本地计算机时是否启用批量压缩。|- 0：禁用 RDP 批量压缩</br>- 1：启用 RDP 批量压缩 | 1 | 是 |
| videoplaybackmode:i:value| 确定连接是否会使用 RDP 高效多媒体流式处理进行视频播放。|- 0：不使用 RDP 高效多媒体流式处理进行视频播放</br>- 1：在可能的情况下使用 RDP 高效多媒体流式处理进行视频播放 | 1 | 是 |

## <a name="device-redirection"></a>设备重定向

| RDP 设置                        | 说明            | 值                 | 默认值          | Windows 虚拟桌面支持 |
|------------------------------------|------------------------|------------------------|:----------------------:|:-----------------------:|
| audiocapturemode:i:value | 麦克风重定向：</br>指明是否已启用音频输入重定向。 | - 0：禁用本地设备的音频捕获</br>- 1：启用本地设备的音频捕获并重定向到远程会话中的音频应用程序 | 0 | 是 |
| encode redirected video capture:i:value | 启用或禁用已重定向视频的编码。 | - 0：禁用已重定向视频的编码</br>- 1：启用已重定向视频的编码 | 1 | 是 |
| redirected video capture encoding quality:i:value | 控制已编码视频的质量。 | - 0：高压缩视频。 当有大量的运动时，质量可能会受到影响。 </br>- 1：中等压缩。</br>- 2：低压缩视频，图片质量高。 | 0 | 是 |
| audiomode:i:value | 音频输出位置：</br>确定本地或远程计算机是否播放音频。 | - 0：在本地计算机上播放音频（在此计算机上播放）</br>- 1：在远程计算机上播放音频（在远程计算机上播放）</br>- 2：不播放声音（不要播放） | 0 | 是 |
| camerastoredirect:s:value | 摄像头重定向：</br>配置要重定向哪些摄像头。 此设置使用分号分隔的列表，其中包含支持重定向的摄像头的 KSCATEGORY_VIDEO_CAMERA 接口。 | - *：重定向所有摄像头</br> - 摄像头列表，如 camerastoredirect:s:\\?\usb#vid_0bda&pid_58b0&mi</br>- 可以通过在符号链接字符串前面加上“-”来排除特定摄像头 | 不重定向任何摄像头 | 是 |
| devicestoredirect:s:value | USB 设备重定向：</br>确定本地计算机上将被重定向并在远程会话中可用的设备。 | - *：重定向所有支持的设备，包括稍后连接的设备</br> - 一个或多个设备的有效硬件 ID | 不重定向任何设备 | 是 |
| drivestoredirect:s:value | 驱动器/存储重定向：</br>确定本地计算机上将被重定向并在远程会话中可用的磁盘驱动器。 | - 未指定值：不重定向任何驱动器</br>- *：重定向所有磁盘驱动器，包括稍后连接的驱动器</br>- DynamicDrives：重定向稍后连接的所有驱动器</br>- 驱动器以及一个或多个驱动器的标签，例如“drivestoredirect:s:C:;E:;”：重定向指定的驱动器 | 不重定向任何驱动器 | 是 |
| redirectclipboard:i:value | 剪贴板重定向：</br>确定是否已启用剪贴板重定向。 | - 0：本地计算机上的剪贴板在远程会话中不可用</br>- 1：本地计算机上的剪贴板在远程会话中可用 | 1 | 是 |
| redirectprinters:i:value | 打印机重定向：</br>确定本地计算机上配置的打印机是否会被重定向并在远程会话中可用 | - 0：本地计算机上的打印机在远程会话中不可用</br>- 1：本地计算机上的打印机在远程会话中可用 | 1 | 是 |
| redirectsmartcards:i:value | 智能卡重定向：</br>确定本地计算机上的智能卡设备是否会被重定向并在远程会话中可用。 |- 0：本地计算机上的智能卡设备在远程会话中不可用</br>- 1：本地计算机上的智能卡设备在远程会话中可用 | 1 | 是 |

## <a name="display-settings"></a>显示设置

| RDP 设置                        | 说明            | 值                 | 默认值          | Windows 虚拟桌面支持 |
|------------------------------------|------------------------|------------------------|:----------------------:|:-----------------------:|
| use multimon:i:value | 确定远程会话是否会使用本地计算机中的一个或多个显示。 | - 0：不启用多显示支持</br>- 1：启用多显示支持 | 0 | 是 |
| selectedmonitors:s:value | 指定要在远程会话中使用的本地显示。 所选的显示必须是连续的。 需要将 use multimon 设置为 1。</br></br>只适用于 Windows 收件箱 (MSTSC) 和 Windows 桌面 (MSRDC) 客户端。 | 特定于计算机的显示 ID 的逗号分隔列表。 可以通过调用 mstsc.exe /l 来检索 ID。 列出的第一个 ID 将被设置为会话中的主显示。 | 所有显示 | 是 |
| maximizetocurrentdisplays:i:value | 确定远程会话在最大化时在哪个显示中进入全屏。 需要将 use multimon 设置为 1。</br></br>只适用于 Windows 桌面 (MSRDC) 客户端。 | - 0：会话在最大化时在最初选择的显示中进入全屏</br>- 1：会话在最大化时在会话窗口所触及的显示中动态进入全屏 | 0 | 是 |
| singlemoninwindowedmode:i:value | 确定多显示远程会话在退出全屏时是否自动切换为单个显示。 需要将 use multimon 设置为 1。</br></br>只适用于 Windows 桌面 (MSRDC) 客户端。 | - 0：会话在退出全屏时保留所有显示</br>- 1：会话在退出全屏时切换为单个显示 | 0 | 是 |
| screen mode id:i:value | 确定远程会话窗口是否在你启动连接时全屏显示。 | - 1：远程会话将在窗口中显示</br>- 2：远程会话将全屏显示 | 2 | 是 |
| smart sizing:i:value | 确定本地计算机是否缩放远程会话的内容来适应窗口大小。 | - 0：本地窗口内容在调整大小时不会缩放</br>- 1：本地窗口内容将在调整大小时缩放 | 0 | 是 |
| dynamic resolution:i:value | 确定在调整本地窗口大小时是否自动更新远程会话的分辨率。 | - 0：会话分辨率在会话期间一直为静态</br>- 1：在调整本地窗口大小时更新会话分辨率 | 1 | 是 |
| desktop size id:i:value | 根据一组预定义选项指定远程会话桌面的尺寸。 如果指定了 desktopheight 和 desktopwidth，则会替代此设置。| -0：640 × 480</br>- 1：800 × 600</br>- 2：1024 × 768</br>- 3：1280 × 1024</br>- 4：1600 × 1200 | 1 | 是 |
| desktopheight:i:value | 指定远程会话的分辨率高度（以像素为单位）。 | 介于 200 和 8192 之间的数值 | 匹配本地计算机 | 是 |
| desktopwidth:i:value | 指定远程会话的分辨率宽度（以像素为单位）。 | 介于 200 和 8192 之间的数值 | 匹配本地计算机 | 是 |
| desktopscalefactor:i:value | 指定远程会话的比例因子，让内容看起来更大。 | 以下列表中的数值：100, 125, 150, 175, 200, 250, 300, 400, 500 | 100 | 是 |

## <a name="remoteapp"></a>RemoteApp

| RDP 设置                        | 说明            | 值                 | 默认值          | Windows 虚拟桌面支持 |
|------------------------------------|------------------------|------------------------|:----------------------:|:-----------------------:|
| remoteapplicationcmdline:s:value | RemoteApp 的可选命令行参数。 | 有效的命令行参数。 | | 否 |
| remoteapplicationexpandcmdline:i:value | 确定 RemoteApp 命令行参数中包含的环境变量应该在本地扩展还是远程扩展。 | - 0：应将环境变量扩展为本地计算机的值</br>- 1：应将环境变量扩展为远程计算机的值 | 1 | 否 |
| remoteapplicationexpandworkingdir:i:value | 确定 RemoteApp 工作目录参数中包含的环境变量应该在本地扩展还是远程扩展。 | - 0：应将环境变量扩展为本地计算机的值</br> - 1：应将环境变量扩展为远程计算机的值。</br>RemoteApp 工作目录通过 shell 工作目录参数指定。 | 1 | 否 |
| remoteapplicationfile:s:value | 指定 RemoteApp 要在远程计算机上打开的文件。</br>若要打开本地文件，还必须为源驱动器启用驱动器重定向。 | 有效文件路径。 | | 否 |
| remoteapplicationicon:s:value | 指定在启动 RemoteApp 时要在客户端 UI 中显示的图标文件。 如果未指定文件名，则客户端将使用标准远程桌面图标。 仅支持“.ico”文件。 | 有效文件路径。 | | 否 |
| remoteapplicationmode:i:value | 确定是否将连接作为 RemoteApp 会话启动。 | - 0：不启动 RemoteApp 会话</br>- 1：启动 RemoteApp 会话 | 1 | 否 |
| remoteapplicationname:s:value | 指定启动 RemoteApp 时客户端界面中的 RemoteApp 名称。| 应用显示名称。 例如，“Excel 2016”。 | | 否 |
| remoteapplicationprogram:s:value | 指定 RemoteApp 的别名或可执行文件名称。 | 有效的别名或名称。 例如，“EXCEL”。 | | 否 |
