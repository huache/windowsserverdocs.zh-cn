---
title: Windows Server 半年频道中对 Nano Server 所做的更改
description: 在全新的 Windows Server servicing 服务模型中，Nano Server 仅作为容器操作系统，且某个功能经过了修改。
ms.mktglfcycl: manage
ms.sitesec: library
author: jasongerend
ms.author: jgerend
ms.localizationpriority: medium
ms.date: 05/21/2019
ms.topic: get-started-article
ms.assetid: a270334d-42a7-46ff-8eed-d8656a276544
ms.openlocfilehash: 6a0f95743a7be890da8aabc2d4fbd2e38a15952f
ms.sourcegitcommit: 5344adcf9c0462561a4f9d47d80afc1d095a5b13
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90766600"
---
# <a name="changes-to-nano-server-in-windows-server-semi-annual-channel"></a>Windows Server 半年频道中对 Nano Server 所做的更改

>适用于：Windows Server 半年频道

如果你已运行 Nano Server，你应该会熟悉 [Window Server 半年频道](../get-started-19/servicing-channels-19.md)服务模式，因为 Nano Server 以前由 Current Branch for Business (CBB) 模型进行了处理。 Windows Server 半年频道只是为相同模型冠以的新名称。 在此模型中，Nano Server 的功能更新发布每年会有两到三次。

但是，自 Windows Server 版本 1803 开始，Nano Server 仅用作**容器基本 OS 映像**。 必须将其作为容器主机中的容器来运行，如 Windows Server 的 Server Core 安装。 在此版本中基于 Nano Server 运行容器与在旧版本中运行的区别如下：

- Nano Server 已经面向 .NET Core 应用程序进行了优化。
- Nano Server 的大小甚至小于 Windows Server 2016 版本。
- 默认情况下，不再包含 PowerShell Core、.NET Core 和 WMI，但在生成容器时，可以包含 [PowerShell Core](https://hub.docker.com/r/microsoft/powershell/) 和 [.NET Core](https://hub.docker.com/r/microsoft/dotnet/) 容器数据包。
- Nano Server 不再包含服务堆栈。 Microsoft 将更新的 Nano 容器发布到你重新部署的 Docker 中心。
- 可以通过使用 Docker 对新的 Nano 容器进行故障排查。
- 现在，可以在 IoT 核心版上运行 Nano 容器。

## <a name="related-topics"></a>相关主题

- [Windows 容器文档](/virtualization/windowscontainers/)
- [Windows Server 半年渠道概述](../get-started-19/servicing-channels-19.md)