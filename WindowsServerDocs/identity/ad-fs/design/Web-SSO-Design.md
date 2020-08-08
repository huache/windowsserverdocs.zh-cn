---
ms.assetid: eb778f63-f7be-438e-8c5e-1fd9b194b967
title: Web SSO 设计
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 7112fe6983a6292c57fc489c959b1edeb0c13c7b
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87949851"
---
# <a name="web-sso-design"></a>Web SSO 设计

在 Active Directory 联合身份验证服务 AD FS 中的 Web 单一 \- 登录 \- \( SSO \) 设计 \( 中 \) ，用户必须只进行一次身份验证，才能访问多个 AD FS \- 安全的应用程序或服务。 在此设计中，所有用户都是外部用户，并且不存在联合信任，因为没有伙伴组织。 通常，当你想要通过 Internet 为单个使用者或客户提供对一个或多个 AD FS 保护的服务或应用程序的访问权限时，你可以部署此设计，如下图所示。

![web sso 设计](media/adfs2_WebSSODesign.gif)

利用 Web SSO 设计，通常 \- 在外围网络中托管 AD FS 保护的应用程序或服务的组织可以在外围网络中维护单独的客户帐户存储，这样可以更轻松地将客户帐户与员工帐户隔离开来。

你可以使用 Active Directory 域服务 \( AD DS \) 、SQL Server 或自定义属性存储来管理外围网络中的客户的本地帐户。

这种设计与 [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)中的部署目标一致。

有关可用于计划和部署 Web SSO 设计的详细任务的列表，请参阅 [Checklist: Implementing a Web SSO Design](../../ad-fs/deployment/Checklist--Implementing-a-Web-SSO-Design.md)。

## <a name="see-also"></a>另请参阅
[Windows Server 2012 中的 AD FS 设计指南](AD-FS-Design-Guide-in-Windows-Server-2012.md)
