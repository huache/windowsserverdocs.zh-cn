---
title: 在 Windows Server Essentials 目标服务器1 上启用文件夹重定向
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
H1: 在 Windows Server Essentials 目标服务器上启用文件夹重定向
ms.assetid: f67d195e-36f6-495a-8361-6d5faa889441
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 9ea3b7b6c42c85ef553e56f017d068fabea42eee
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622870"
---
# <a name="enable-folder-redirection-on-the-windows-server-essentials-destination-server1"></a>在 Windows Server Essentials 目标服务器1 上启用文件夹重定向

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

如果在源服务器上启用了文件夹重定向，则可以执行此任务。

 首先，使用 Windows Server Essentials 仪表板在目标服务器上启用文件夹重定向。 然后，删除旧的文件夹重定向组策略设置。

### <a name="to-enable-folder-redirection-on-the-destination-server"></a>在目标服务器上启用文件夹重定向

1.  在目标服务器上，打开 Windows Server Essentials 仪表板。

2.  在导航栏中，单击“设备”****。

3.  在“设备任务”**** 窗格中，单击“实现组策略”****。

4.  在“启用文件夹重定向组策略”**** 页上，选择要重定向的文件夹，然后单击“下一步”****。

5.  在“启用安全策略设置”**** 页上，单击“完成”****。

### <a name="to-delete-the-old-folder-redirection-group-policy-setting"></a>删除旧的文件夹重定向组策略设置

1. 在目标服务器上，打开“组策略管理”**** 管理工具。

2. 在 **组策略管理**"中，依次展开" **林：**<em>YourNetworkDomainName</em>"、" **域**"、" *YourNetworkDomainName*"，然后展开" **组策略对象**"。

3. 右键单击“W7PVP 文件夹重定向”****，然后单击“删除”****。

4. 阅读警告，然后单击“是”****。

5. 关闭“组策略管理”  。

   若要将更改应用于文件夹重定向，则网络用户必须注销其计算机，然后再重新登录。 这可确保所有重定向的文件夹都传输到目标服务器。
