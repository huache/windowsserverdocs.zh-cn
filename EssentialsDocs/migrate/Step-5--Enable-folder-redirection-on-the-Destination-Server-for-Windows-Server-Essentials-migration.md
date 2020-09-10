---
title: 步骤 5：在目标服务器上启用文件夹重定向以进行 Windows Server Essentials 迁移
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: d3925f80-552d-431f-b2a6-2af202e50ca4
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 2fa628429a692f77620116ed0db2ef052abc8a22
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625445"
---
# <a name="step-5-enable-folder-redirection-on-the-destination-server-for-windows-server-essentials-migration"></a>步骤 5：在目标服务器上启用文件夹重定向以进行 Windows Server Essentials 迁移

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials

如果在源服务器上启用了文件夹重定向，则可以在目标服务器上也启用同样功能，然后删除旧的“文件夹重定向组策略”设置。

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

3. 右键单击要删除的策略，然后单击“删除”****。

4. 阅读警告，然后单击“是”****。

5. 关闭“组策略管理”  。

   若要将更改应用于文件夹重定向，则网络用户必须注销其计算机，然后再重新登录。 这可确保所有重定向的文件夹都传输到目标服务器。

## <a name="next-steps"></a>后续步骤
 已在目标服务器上启用文件夹重定向。 现在，请跳到 [步骤6：从新的 Windows Server Essentials 网络降级和删除源服务器](Step-6--Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md)。


若要查看所有步骤，请参阅 [迁移到 Windows Server Essentials](Migrate-from-Previous-Versions-to-Windows-Server-Essentials-or-Windows-Server-Essentials-Experience.md)。

