---
title: Windows 桌面客户端中的新功能
description: 了解 Windows 桌面的远程桌面客户端的最新更改
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 01/29/2020
ms.localizationpriority: medium
ms.openlocfilehash: b2d5215c7089ce1aadbeae68890dca1a0ae1c294
ms.sourcegitcommit: 9077469e372d2aafcad890cbc4e4a24c58a3838c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2020
ms.locfileid: "76889441"
---
# <a name="whats-new-in-the-windows-desktop-client"></a>Windows 桌面客户端中的新功能

有关 Windows 桌面客户端的更多详细信息，可参阅 [Windows 桌面客户端入门](windowsdesktop.md)。 可在下面找到客户端的最新更新。

## <a name="latest-client-versions"></a>最新客户端版本

可以针对不同的[用户组](windowsdesktop-admin.md#configure-user-groups)来配置客户端。 下表列出了适用于每个用户组的当前版本：

|用户组 |版本  |
|-----------|---------|
|公用     |1.2.605  |
|Insider    |1.2.605  |

## <a name="updates-for-version-12605"></a>针对版本 1.2.605 的更新

*发布日期：2020/01/29*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4oHrD)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4oJZs)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4oXhD)

- 现在可以选择要用于桌面连接的显示器。 若要更改此设置，请右键单击桌面连接的图标，然后选择“设置”  。
- 修复了连接设置未显示正确的可用缩放系数的问题。
- 修复了讲述人无法读取连接启动时显示的对话框的问题。
- 修复了在 Azure Active Directory 名称和 Active Directory 名称不匹配时显示错误用户名的问题。
- 修复了在未连接网络的情况下启动连接时客户端停止响应的问题。
- 修复了在附加耳机时导致客户端停止响应的问题。

## <a name="updates-for-version-12535"></a>针对版本 1.2.535 的更新

*发布日期：2019/12/04*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4k7jH)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4k7jL)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4k27O)

- 你现在可以直接通过客户端顶部命令栏上的“更多选项”按钮访问有关更新的信息。
- 你现在可以从客户端的命令栏报告反馈。
- 现在，“反馈”选项仅在反馈中心可用的情况下显示。
- 确保在通过策略禁用通知的情况下不显示更新通知。
- 修复了妨碍某些 RDP 文件启动的问题。
- 修复了在启动客户端时发生崩溃的问题，该问题是某些持久性设置受损导致的。

## <a name="updates-for-version-12431"></a>针对版本 1.2.431 的更新

*发布日期：2019/11/12*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE48kow)、[Windows 32 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE48koA)、[Windows ARM64](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE48zYj)

- 客户端的 32 位版和 ARM64 版现已提供！
- 客户端现在会保存你对连接栏所做的任何更改（例如，其位置、大小和固定状态），并跨会话应用这些更改。
- 更新的网关信息和连接状态对话框。
- 解决了已导致在 Azure Active Directory 令牌过期后尝试连接时两个凭据同时提示的问题。
- 现在，在 Windows 7 中，如果用户已保存凭据而服务器不接受该凭据时，系统会正确提示用户输入凭据。
- 重新连接时，Azure Active Directory 提示现在会显示在连接窗口的前面。
- 固定到任务栏的项现在会在源刷新过程中更新。
- 已改进在使用触控时连接中心上进行的滚动。
- 从“分辨率”下拉菜单中删除了空行。
- 在 Windows 凭据管理器中删除了不必要的条目。
- 现在，在退出全屏时，桌面会话的大小会正确调整。
- 现在，当进入睡眠模式后恢复会话时，“RemoteApp 断开连接”对话框会显示在前台。
- 解决了辅助功能问题，如键盘导航。

## <a name="updates-for-version-12247"></a>针对版本 1.2.247 的更新

*发布日期：2019/09/17*

下载：[Windows 64 位](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE3LkSa)

- 改进了本地化版本的回退语言。 （例如，FR-CA 将以法语正确显示，而不是以英语显示。）
- 删除订阅时，客户端现在会从凭据管理器中正确删除保存的凭据。
- 现在，客户端更新过程在启动后无人参与的情况下完成，并且将在完成后重新启动客户端。
- 现在可以在 Windows 10 上以 S 模式使用客户端。
- 修复了一个问题，对于用户名中有一个空格的用户，该问题会导致更新过程失败。
- 修复了在连接过程中进行身份验证时发生的崩溃问题。
- 修复了在关闭客户端时发生的崩溃问题。
