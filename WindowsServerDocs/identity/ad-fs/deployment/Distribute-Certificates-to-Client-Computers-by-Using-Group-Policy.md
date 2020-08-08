---
ms.assetid: cf32926a-2083-408b-a264-2cad179ed18a
title: 使用组策略将证书分发到客户端计算机
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 35b543a7a249130d1fd66a0d86424b5bcb0b8d96
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87962891"
---
# <a name="distribute-certificates-to-client-computers-by-using-group-policy"></a>使用组策略将证书分发到客户端计算机


你可以使用以下过程向下推送适用于帐户 \( \) \( \) 联合服务器、资源联合服务器和 Web 服务器与帐户伙伴林中每台客户端计算机之间的相应安全套接字层 SSL 证书或等效证书，方法是使用组策略。

**Domain admins**或**Enterprise Admins**中的成员身份或同等身份 Active Directory 域服务 \( AD DS \) 是完成此过程的最低要求。  有关使用适当帐户和组成员身份的详细信息，请参阅[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477) \( http： \/ \/ go.microsoft.com \/ fwlink \/ ？LinkId \= 83477 \) 。

### <a name="to-distribute-certificates-to-client-computers-by-using-group-policy"></a>使用组策略将证书分发到客户端计算机

1.  在帐户伙伴组织的林中的域控制器上，启动**组策略管理**"管理单元 \- 。

2.  查找现有组策略对象 \( GPO \) ，或创建新的 gpo 以包含证书设置。 确保 GPO 与 \( \) 相应的用户和计算机帐户所在的域、站点或组织单位 OU 相关联。

3.  右键 \- 单击该 GPO，然后单击 "**编辑**"。

4.  在控制台树中，打开 "**计算机配置 \\ 策略 Windows 设置" "安全设置" " \\ \\ \\ 公钥策略**"，右键 \- 单击 "**受信任的根证书颁发机构**"，然后单击 "**导入**"。

5.  在 "**欢迎使用证书导入向导**" 页上，单击 "**下一步**"。

6.  在 "**要导入的文件**" 页上，键入相应的证书文件的路径 \( （例如 \\ \\ fs1 \\ c $ \\ Fs1 \) ），然后单击 "**下一步**"。

7.  在 "**证书存储**" 页上，单击 **"将所有证书放入下列存储**"，然后单击 "**下一步**"。

8.  在 "**正在完成证书导入向导**" 页上，验证提供的信息是否正确，然后单击 "**完成**"。

9. 重复步骤2到步骤6，为场中的每台联合服务器添加其他证书。
