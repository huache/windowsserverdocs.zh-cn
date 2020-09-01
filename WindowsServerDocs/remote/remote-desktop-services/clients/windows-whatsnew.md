---
title: Windows 应用商店客户端中的新增功能
description: 了解适用于 Windows 应用商店的远程桌面客户端的最新更改
ms.topic: article
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 08/26/2020
ms.localizationpriority: medium
ms.openlocfilehash: 56e2a5f91983f8fe64382e162ecf18b30e75b41d
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88938787"
---
# <a name="whats-new-in-the-windows-store-client"></a>Windows 应用商店客户端中的新增功能

我们会定期更新 [Microsoft Store 客户端](windows.md)，添加新功能并修复问题。 可在下面找到最新更新。

## <a name="updates-for-version-1021522"></a>针对版本 10.2.1522 的更新

*发布日期：2020/08/26*

- 重写了客户端，使其使用与 iOS、macOS 和 Android 客户端相同的基础 RDP 核心引擎。
- 现支持 Windows 虚拟桌面的 Windows 资源管理器集成版本。
- 添加了对 x64 和 ARM64 的支持。
- 将侧面板设计更新为了全屏。
- 添加了对浅色模式和深色模式的支持。
- 添加了订阅和连接到主权云部署的功能。
- 添加在正式发布 (RTM) 时启用和还原工作区（书签）的功能。
- 更新了在订阅过程中使用现有 Azure Active Directory (Azure AD) 令牌减少用户必须登录的次数的功能。
- 更新后的订阅现可检测你是在使用 Windows 虚拟桌面还是 Windows 虚拟桌面（经典）。
- 解决了将文件复制到远程电脑方面的问题。
- 解决了按钮方面的常见辅助功能问题。

## <a name="updates-for-version-1011215"></a>针对版本 10.1.1215 的更新

*发布日期：2020 年 4 月 20 日*

- 更新了 Windows 虚拟桌面的用户代理字符串。

## <a name="updates-for-version-1011195"></a>针对版本 10.1.1195 的更新

*发布日期：2020 年 3 月 6 日*

- 现在，即使应用已最小化或在后台运行，会话中的音频也可以继续播放。
- 修复了在本地电脑和远程电脑之间切换键（CAPS LOCK、Num Lock 等）不同步的问题。
- 64 位设备上的性能改进。
- 修复了在应用挂起时发生崩溃的问题。

## <a name="updates-for-version-1011107"></a>针对版本 10.1.1107 的更新

*发布日期：2019/9/4*

- 现在可以在本地和远程电脑之间复制文件。
- 现在可以使用你的电子邮件地址访问远程资源（如果你的管理员已启用此功能）。
- 现在可以更改远程资源源的用户帐户分配。
- 应用现在会在文件资源管理器中显示分配给此应用的 .rdp 文件的正确图标，而不是空的默认图标。

## <a name="updates-for-version-1011098"></a>针对版本 10.1.1098 的更新

*发布日期：2019 年 3 月 15 日*

- 现在可以设置用户帐户的显示名称，这样可以用不同的密码保存相同用户名。
- 添加远程资源时，现可选择现有用户帐户。
- 修复了客户端未正确终止的问题。
- 客户端现在可以正确处理辅助窗口打开时的挂起问题。
- 其他 bug 修复。

## <a name="updates-for-version-1011088"></a>针对版本 10.1.1088 的更新

*发布日期：2018 年 11 月 6 日*

- 连接显示名称现在更易于发现。
- 修复了连接仍处于活动状态期间关闭客户端窗口时崩溃的问题。
- 修复了客户端最小化后重新连接时的挂起问题。
- 允许将桌面拖放到组中的任何位置。
- 确保在需要时从跳转列表启动连接会生成一个单独的窗口。
- 其他 bug 修复。

## <a name="updates-for-version-1011060"></a>针对版本 10.1.1060 的更新

*发布日期：2018 年 9 月 14 日*

- 解决了双击桌面连接导致启动两个会话的问题。
- 修复了在本地虚拟桌面之间进行切换时的崩溃问题。
- 现将会话移动到另一个监视器还会更新会话比例系数。
- 处理其他系统密钥，如 AltGr。
- 其他 bug 修复。

## <a name="updates-for-version-1011046"></a>针对版本 10.1.1046 的更新

*发布日期：2018 年 6 月 20 日*

- Bug 修复。

## <a name="updates-for-version-1011042"></a>针对版本 10.1.1042 的更新

*发布日期：2018 年 4 月 2 日*

- 用于解决 CVE-2018-0886 中所述的 CredSSP 加密 Oracle 修正的更新。
- 其他 bug 修复。
