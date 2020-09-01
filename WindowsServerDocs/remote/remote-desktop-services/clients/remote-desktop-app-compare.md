---
title: 远程桌面 - 比较客户端应用
description: 了解不同 RD 应用在支持的特性和功能方面的比较。
ms.topic: article
ms.assetid: 12efe858-6b76-4e08-9f72-b9603aceb0fc
author: heidilohr
manager: lizross
ms.author: helohr
ms.date: 08/25/2020
ms.localizationpriority: medium
ms.openlocfilehash: a44926d50fae9dea38e3f5c46db423991a414a87
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88941507"
---
# <a name="compare-the-clients"></a>比较客户端

>适用于：Windows 10、Windows 8.1、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2

我们经常被问及不同远程桌面客户端应用彼此相比如何。 它们是否都执行相同的操作？ 以下是这些问题的答案。

## <a name="redirection-support"></a>重定向支持

下表比较了不同客户端对设备和其他重定向的支持。 这些表涵盖了可以在远程会话中访问一次的重定向。

如果远程连接到个人桌面，可在会话的“其他设置”  中配置其他重定向。 如果远程桌面或应用由组织管理，则管理员可以通过“组策略”设置或 RDP 属性启用或禁用重定向。

### <a name="input-redirection"></a>输入重定向

| 重定向 | Windows 收件箱</br>(MSTSC) | Windows 桌面</br>(MSRDC) | Windows 应用商店 | Android | iOS | macOS | Web 客户端    |
|-------------|---------------------------|-----------------------------|---------------|---------|-----|-------|---------------|
| Keyboard    | X                         | X                           | X             | X       | X   | X     | X             |
| 鼠标       | X                         | X                           | X             | X       | X\* | X     | X             |
| 触摸       | X                         | X                           | X             | X       | X   |       | X（IE 除外） |
| 笔         | X                         | X                           |               | X（与触控相同） |  X（与触控相同）  |       |               |

*请查看[远程桌面 iOS 客户端支持的输入设备列表](remote-desktop-ios.md#supported-input-devices)。

### <a name="port-redirection"></a>端口重定向

| 重定向 | Windows 收件箱</br>(MSTSC) | Windows 桌面</br>(MSRDC) | Windows 应用商店 | Android | iOS | macOS | Web 客户端 |
|-------------|---------------------------|-----------------------------|---------------|---------|-----|-------|------------|
| 串行端口 | X                         | X                           |               |         |     |       |            |
| USB         | X                         | X                           |               |         |     |       |            |

启用 USB 端口重定向时，会自动在远程会话中识别连接到 USB 端口的任何 USB 设备。

### <a name="other-redirection-devices-etc"></a>其他重定向（设备等）

| 重定向         | Windows 收件箱</br>(MSTSC) | Windows 桌面</br>(MSRDC) | Windows 应用商店 | Android | iOS         | macOS                           | Web 客户端    |
|---------------------|---------------------------|-----------------------------|---------------|---------|-------------|---------------------------------|---------------|
| 相机             | X                         | X                           |               |     X    |   X         | X                               |               |
| 剪贴板           | X                         | X                           | X             | 文本    | 文本、图像 | X                               | 文本          |
| 本地驱动器/存储 | X                         | X                           |               | X       |   X        | X                               |               |
| 位置            | X                         | X                           |               |         |             |                                 |               |
| 麦克风         | X                         | X                           | X             |         |  X          | X                               |               |
| 打印机            | X                         | X                           |               |         |             | X（仅 CUPS）                   | PDF 打印     |
| 扫描仪            | X                         | X                           |               |         |             |                                 |               |
| Smart Cards         | X                         | X                           |               |         |             | X（不支持 Windows 登录） |               |
| 扬声器            | X                         | X                           | X             | X       | X           | X                               | X（IE 除外） |

*对于打印机重定向 - macOS 应用默认情况下支持 Publisher Imagesetter 打印机驱动程序。 它们不支持重定向本机打印机驱动程序。
