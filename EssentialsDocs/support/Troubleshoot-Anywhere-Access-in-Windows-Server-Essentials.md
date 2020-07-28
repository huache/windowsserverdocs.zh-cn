---
title: Windows Server Essentials 中的随处访问疑难解答
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 68f2b05c-09eb-4cba-8db4-a91353b513c6
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 3e79a4e7845298b013d99ff804c665e44cac4fbb
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87180333"
---
# <a name="troubleshoot-anywhere-access-in-windows-server-essentials"></a>Windows Server Essentials 中的随处访问疑难解答

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

本主题提供有关使用 Windows Server Essentials 中的修复随处访问向导解决阻止网络用户访问服务器资源问题的常规说明。 随处访问功能-远程 Web 访问、虚拟专用网络（VPN）和 DirectAccess）使网络用户能够随时从任何设备通过 Internet 连接访问服务器资源。

修复随处访问向导将尝试标识并修复路由器、域名或防火墙的问题，这些问题阻止了网络用户远程访问服务器资源。

> [!NOTE]
> 有关 Windows Server Essentials 社区中的最新疑难解答信息，建议访问[Windows Server Essentials 论坛](https://docs.microsoft.com/answers/topics/windows-server-essentials.html)。 Windows Server Essentials 论坛是寻求帮助或提出问题的好地方。

## <a name="to-repair-anywhere-access"></a>修复随处访问

1. 登录到服务器，然后打开仪表板。

2. 单击“设置”****，然后单击“随处访问”**** 选项卡。

3. 单击“修复”****。 修复随处访问向导将启动。

4. 单击“下一步”。 该向导将分析随处访问、标识问题并尝试修复问题。

5. 如果你在向导完成后收到一个警报，你可以单击“重试”**** 以尝试重新修复问题。 如果你仍收到警报，请检查该警报以获取有关问题和疑难解答步骤的其他信息。

## <a name="to-get-more-information-about-an-alert"></a>获取有关警报的详细信息

1. 在仪表板的右上角，单击任意错误或警告图标以打开警报查看器。

2. 在警报查看器中，单击错误或警告以查看其他信息。

## <a name="additional-troubleshooting-for-anywhere-access"></a>随处访问的其他疑难解答
 如果修复随处访问向导无法修复随处访问，请检查以下疑难解答资源（针对与远程 Web 访问、VPN 和 DirectAccess 相关的问题）：

- [远程 Web 访问连接疑难解答](Troubleshoot-Remote-Web-Access-connectivity-in-Windows-Server-Essentials.md)

- [防火墙疑难解答](Troubleshoot-your-firewall-in-Windows-Server-Essentials.md)

- 查看[Windows Server Essentials 论坛](https://docs.microsoft.com/answers/topics/windows-server-essentials.html)，了解 Windows server essentials 社区报告的最新问题。
