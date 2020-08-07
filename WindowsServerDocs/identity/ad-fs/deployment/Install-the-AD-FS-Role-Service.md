---
ms.assetid: c28a1b8b-5bec-4eed-8c95-a1a29cfc957c
title: 安装 AD FS 角色服务
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 435634e7b6edfc110c7bd208d727b974804eb236
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87972174"
---
# <a name="install-the-ad-fs-role-service"></a>安装 AD FS 角色服务

你可以使用以下过程在运行 Windows Server 2012 R2 的计算机上安装 AD FS 角色服务，以便成为联合服务器场中的第一个联合服务器或现有联合服务器场中的联合服务器。

在本地计算机上， **Administrators**中的成员身份或同等身份是完成此过程的最低要求。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

### <a name="to-install-the-ad-fs-server-role-via-the-add-roles-and-features-wizard"></a>通过添加角色和功能向导安装 AD FS 服务器角色

1.  打开服务器管理器。 若要打开服务器管理器，请在 "**开始**" 屏幕上单击 "**服务器管理器**"，或者在桌面上的任务栏中单击 "**服务器管理器**"。 在 **“仪表板”** 页上的 **“欢迎”** 磁贴的 **“快速启动”** 选项卡中，单击 **“添加角色和功能”**。 或者，也可以在“管理”**** 菜单中单击“添加角色和功能”****。

2.  在“开始之前”  页上，单击“下一步”  。

3.  在 "**选择安装类型**" 页上，单击 " ** \- 基于角色或基于功能的 \- 安装**"，然后单击 "**下一步**"。

4.  在“选择目标服务器”**** 页面上，单击“从服务器池中选择一个服务器”****，验证目标计算机是否已选中，然后单击“下一步”****。

5.  在 **“选择服务器角色”** 页上，单击 **“Active Directory 联合身份验证服务”**，然后单击 **“下一步”**。

6.  在“选择功能”**** 页上，单击“下一步”****。 为您预先选择了所需的必备组件。 不需要选择任何其他功能。

7.  在 " **Active Directory 联合身份验证服务 \( AD FS \) ** " 页上，单击 "**下一步**"。

8.  确认 **“确认安装选择”** 页上的信息后，单击 **“安装”**。

9. 在 **“安装进度”** 页上，确认已正确安装所有项目，然后单击 **“关闭”**。

### <a name="to-install-the-ad-fs-server-role-via-windows-powershell"></a>通过 Windows PowerShell 安装 AD FS 服务器角色

1.  在要配置为联合服务器的计算机上，打开 Windows PowerShell 命令窗口，然后运行以下命令： `Install-windowsfeature adfs-federation –IncludeManagementTools` 。

## <a name="see-also"></a>另请参阅

[AD FS 部署](../../ad-fs/AD-FS-Deployment.md)

[Windows Server 2012 R2 AD FS 部署指南](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)

[部署联合服务器场](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)


