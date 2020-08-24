---
title: Windows Server 2019 中的 Windows 时间服务功能的内部预览
description: Windows Server 2019 中的新 Windows 时间服务功能
author: dahavey
ms.author: dahavey
ms.date: 06/06/2020
ms.topic: article
ms.openlocfilehash: 01968fe51d25f394e346cebc8dbeafd2dd17ca4a
ms.sourcegitcommit: b5b040a47cf48c94852de9aad8b91475f891d2f7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88563367"
---
# <a name="insider-preview"></a>内部预览


## <a name="leap-second-support"></a>闰秒支持

> 适用于：Windows Server 2019 和 Windows 10 版本 1809

闰秒是 UTC 偶尔的 1 秒调整。 随着地球自转速度的降低，[UTC](https://en.wikipedia.org/wiki/Coordinated_Universal_Time)（原子时间刻度）会偏离[平均太阳时间](https://en.wikipedia.org/wiki/Solar_time#Mean_solar_time)或天文时间。 在 UTC 最多偏离 .9 秒时，将插入[闰秒](https://en.wikipedia.org/wiki/Leap_second)以保持 UTC 与平均太阳时间同步。

闰秒对于满足美国和欧盟在准确性和可追溯性方面的监管要求已经变得非常重要。

有关更多信息，请参阅：

- 我们的[公告博客](https://techcommunity.microsoft.com/t5/networking-blog/top-10-networking-features-in-windows-server-2019-10-accurate/ba-p/339739/)

- 适用于[开发人员](https://aka.ms/Dev-LeapSecond)的验证指南

- 适用于 [IT 专业人员](https://aka.ms/ITPro-LeapSecond)的验证指南


## <a name="precision-time-protocol"></a>精确时间协议

> 适用于：Windows Server 2019 和 Windows 10 版本 1809

借助 Windows Server 2019 和 Windows 10（版本 1809）中包含的新时间提供程序，用户可使用精确时间协议 (PTP) 来同步时间。 随着时间在网络上分配，它会遇到延迟，如果不考虑延迟，或者如果延迟不是对称的，就会越来越难以理解从时间服务器发送的时间戳。 PTP 使网络设备能够将每个网络设备引入的延迟添加到计时测量，从而为 Windows 客户端提供更准确的时间示例。

有关更多信息，请参阅：

- 我们的[公告博客](https://techcommunity.microsoft.com/t5/networking-blog/top-10-networking-features-in-windows-server-2019-10-accurate/ba-p/339739/)

- 适用于 [IT 专业人员](https://aka.ms/PTPValidation)的验证指南


## <a name="software-timestamping"></a>软件时间戳

> 适用于：Windows Server 2019 和 Windows 10 版本 1809

从时间服务器通过网络接收计时数据包时，必须先由操作系统的网络堆栈对其进行处理，然后再将其用于时间服务。 网络堆栈中的每个组件都会引入可变数量的延迟，这会影响计时测量的准确性。

![软件时间戳](../media/Windows-Time-Service/software-timestamping.png)

为了解决此问题，我们可以借助软件时间戳在上面显示的“Windows 网络组件”之前和之后向数据包添加时间戳，以解决操作系统中的延迟问题。

有关更多信息，请参阅：

- 我们的[公告博客](https://techcommunity.microsoft.com/t5/networking-blog/top-10-networking-features-in-windows-server-2019-10-accurate/ba-p/339739/)

- [面向开发人员和 IT 专业人员的验证指南](https://github.com/microsoft/W32Time/tree/master/Leap%20Seconds)


---
