---
ms.assetid: bbb5b68f-00ad-4715-8176-0c2769b706c4
title: Windows Server 2012 R2 AD FS 部署指南
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 70818fffb601d7da6b9e7e6f8a1e2a774abf2ca5
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86965479"
---
# <a name="deploying-a-federation-server-farm"></a>部署联合服务器场


若要部署联合服务器场，请按顺序完成此清单中的任务。 引用链接你将转到概念主题时，请在查看概念主题后返回到此清单，以便可以继续执行此清单中的剩余任务。  
  
![部署联合服务器场](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**清单：部署联合服务器场**  
  
||任务|参考|  
|-|--------|-------------|  
|![部署联合服务器场](media/icon_checkboxo.gif)|准备部署 Active Directory 联合身份验证服务 AD FS 时，请查看重要的概念和注意事项 \( \) 。 **注意：**|![](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[在 Windows server 2012 R2 中](../../ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)部署联合服务器场 AD FS 设计指南<p>![部署联合服务器场](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[了解密钥 AD FS 概念](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)|  
||如果决定将 Microsoft SQL Server 用于 AD FS 配置存储，请确保部署 SQL Server 的功能实例。|[SQL Server](/sql/sql-server/?view=sql-server-ver15) **警告：** 在 Windows Server 2012 R2 中，如果要创建 AD FS 场并使用 SQL Server 存储配置数据，可以使用 SQL Server 2008 和更新版本，包括 SQL Server 2012。|  
|![部署联合服务器场](media/icon_checkboxo.gif)|将计算机加入 Active Directory 域。|![部署联合服务器场](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[将计算机加入域](Join-a-Computer-to-a-Domain.md)|  
|![部署联合服务器场](media/icon_checkboxo.gif)|注册 AD FS 的安全套接字层 \( SSL \) 证书。|![部署联合服务器场](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[注册 AD FS 的 SSL 证书](Enroll-an-SSL-Certificate-for-AD-FS.md)|  
|![部署联合服务器场](media/icon_checkboxo.gif)|安装 AD FS 角色服务。|![部署联合服务器场](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[安装 AD FS 角色服务](Install-the-AD-FS-Role-Service.md)|  
|![部署联合服务器场](media/icon_checkboxo.gif)|配置联合服务器。|![部署联合服务器场](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[配置联合服务器](Configure-a-Federation-Server.md)|  
|![部署联合服务器场](media/icon_checkboxo.gif)|可选步骤：使用设备注册服务 DRS 配置联合服务器 \( \) 。|![部署联合服务器场](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[使用设备注册服务配置联合服务器](Configure-a-federation-server-with-Device-Registration-Service.md)|  
|![部署联合服务器场](media/icon_checkboxo.gif)|向 \( \) \( \) \( \) 联合身份验证服务和 DRS 的公司域名系统 DNS 添加主机 a 和别名 CNAME 资源记录。|![部署联合服务器场](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[为联合身份验证服务和 DRS 配置企业 DNS](Configure-Corporate-DNS-for-the-Federation-Service-and-DRS.md)|  
|![部署联合服务器场](media/icon_checkboxo.gif)|验证联合服务器是否正常运行。|![部署联合服务器场](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[验证联合服务器是否正常工作](Verify-That-a-Federation-Server-Is-Operational.md)|  
  

## <a name="see-also"></a>另请参阅  
[AD FS 部署](../../ad-fs/AD-FS-Deployment.md)  

[Windows Server 2012 R2 AD FS 部署指南](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
  
