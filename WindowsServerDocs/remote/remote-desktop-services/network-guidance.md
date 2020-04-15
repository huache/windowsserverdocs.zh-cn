---
title: 网络指南
description: 针对远程桌面部署的带宽建议。
ms.prod: windows-server
ms.technology: remote-desktop-services
ms.author: helohr
ms.date: 12/12/2019
ms.topic: article
author: Heidilohr
manager: lizross
ms.openlocfilehash: 79db56d467ae0913446faebffc5a9598aae0b767
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852990"
---
# <a name="network-guidance"></a>网络指南

使用远程 Windows 会话时，网络的可用带宽会极大地影响你的体验质量。 不同的应用程序和显示分辨率需要不同的网络配置，因此，请务必确保已对网络进行了配置以满足你的需求。

>[!NOTE]
>以下建议适用于损失低于 0.1% 的网络。 无论在虚拟机 (VM) 上托管多少会话，这些建议均适用。

## <a name="applications"></a>应用程序

下表列出了建议的最小带宽，保证流畅的用户体验。 这些建议基于[远程桌面工作负荷](remote-desktop-workloads.md)中的准则。

| 工作负荷类型   | 建议带宽 |
|-----------------|-----------------------|
| 轻型           | 1.5 Mbps              |
| 中          | 3 Mbps                |
| 重型           | 5 Mbps                |
| 强力           | 15 Mbps               |

请记住，施加于网络的压力取决于应用工作负荷的输出帧速率和显示分辨率。 如果帧速率或显示分辨率提高，带宽要求也会随之提高。 例如，具有高分辨率显示的一个轻型工作负荷比具有常规或低分辨率的轻型工作负荷需要更多的可用带宽。

其他方案的带宽要求可能会根据你的使用方式而发生更改，例如：

- 语音或视频会议
- 实时通信
- 流式处理 4K 视频

请确保使用 Login VSI 等模拟工具在部署中对这些方案进行负载测试。 在远程会话中改变负载大小、运行压力测试以及测试常见用户方案，从而更好地了解你的网络需求。

## <a name="display-resolutions"></a>显示分辨率

不同的显示分辨率需要不同的可用带宽。 下表列出了我们建议的带宽，实现在典型的显示分辨率下以每秒 30 帧 (fps) 的帧速率保证流畅的用户体验。 这些建议适用于单个和多个用户方案。 请记住，涉及帧速率在 30 fps 以下的方案（例如读取静态文本）需要较少的可用带宽。

| 30 fps 下典型的显示分辨率    | 建议带宽 |
|------------------------------------------|-----------------------|
| 约 1024 × 768 像素                      | 1.5 Mbps              |
| 约 1280 × 720 像素                      | 3 Mbps                |
| 约 1920 × 1080 像素                     | 5 Mbps                |
| 约 3840 × 2160 像素 (4K)                | 15 Mbps               |

## <a name="additional-resources"></a>其他资源

你所在的 Azure 区域可能会像影响网络条件一样影响用户体验。 请查看 [Windows 虚拟桌面体验估算器](https://azure.microsoft.com/services/virtual-desktop/assessment/)以了解详细信息。
