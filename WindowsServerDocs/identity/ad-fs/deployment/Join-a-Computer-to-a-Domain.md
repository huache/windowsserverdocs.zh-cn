---
ms.assetid: 10d6723e-c857-43da-9d2d-acb5641d3da8
title: 将计算机加入域
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: edb02a623998f2bac3621f201267e76fdcf3e1dd
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969744"
---
# <a name="join-a-computer-to-a-domain"></a>将计算机加入域

要使 Active Directory 联合身份验证服务 \( AD FS \) 运行，必须将充当联合服务器的每台计算机加入域。 联合服务器代理可以加入到域中，但这不是必需的。

如果 Web 服务器仅承载声明感知应用程序，则无需将 Web 服务器加入域 \- 。

若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

### <a name="to-join-a-computer-to-a-domain"></a>将计算机加入域

1.  在 "**开始**" 屏幕上，键入 **"控制面板**"，然后按 enter。

2.  导航到 "**系统和安全**"，然后单击 "**系统**"。

3.  在“计算机名、域和工作组设置”**** 下，单击“更改设置”****。

4.  在“计算机名”**** 选项卡上，单击“更改”****。

5.  在 "**隶属于**" 下，单击 "**域**"，键入希望此计算机加入的域的名称，然后单击 **"确定"**。

6.  单击 **“确定”**，然后重新启动计算机。

## <a name="additional-references"></a>其他参考
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)

[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)


