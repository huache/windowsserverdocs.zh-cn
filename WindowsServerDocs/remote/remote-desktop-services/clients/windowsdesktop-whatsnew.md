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
manager: daveba
ms.author: helohr
ms.date: 10/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: 6a8e66398bc61a69250b84101a3cb66f2c8f3548
ms.sourcegitcommit: 1da993bbb7d578a542e224dde07f93adfcd2f489
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73567070"
---
# <a name="whats-new-in-the-windows-desktop-client"></a>Windows 桌面客户端中的新功能

有关 Windows 桌面客户端的更多详细信息，可参阅 [Windows 桌面客户端入门](windowsdesktop.md)。 可在下面找到客户端的最新更新。

## <a name="latest-client-versions"></a>最新客户端版本

可以针对不同的[用户组](windowsdesktop-admin.md#configure-user-groups)来配置客户端。 下表列出了适用于每个用户组的当前版本：

|用户组 |版本  |
|-----------|---------|
|Public     |1.2.247  |
|预览体验成员    |1.2.428  |

## <a name="updates-for-version-12428"></a>针对版本 1.2.428 的更新

*发布日期：2019/10/31*

- 客户端的 32 位和 ARM64 版的预览版现已提供！
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

- 修复了在连接过程中进行身份验证时发生的崩溃问题。
- 修复了在关闭客户端时发生的崩溃问题。

## <a name="updates-for-version-12246"></a>针对版本 1.2.246 的更新

*发布日期：2019 年 8 月 28 日*

- 改进了本地化版本的回退语言。 （例如，FR-CA 将以法语正确显示，而不是以英语显示。）
- 删除订阅时，客户端现在会从凭据管理器中正确删除保存的凭据。
- 现在，客户端更新过程在启动后无人参与的情况下完成，并且将在完成后重新启动客户端。
- 现在可以在 Windows 10 上以 S 模式使用客户端。
- 修复了一个问题，对于用户名中有一个空格的用户，该问题会导致更新过程失败。
