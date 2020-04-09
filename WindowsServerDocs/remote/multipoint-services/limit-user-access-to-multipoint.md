---
title: 限制用户对服务器的访问
description: 了解如何为用户和组授予或拒绝对 MultiPoint 服务的访问权限
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 4cabd4f1-a764-4be6-bc6e-0a5f5566390c
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: ddc852eea3ed17cd354cc87c79d82066f989bd5d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80820250"
---
# <a name="limit-users-access-to-the-multipoint-server"></a>限制用户对 Multipoint 服务器的访问
无论是将 MultiPoint server 联接到 Active Directory 域还是使用本地用户帐户，默认情况下，所有用户都有权访问 MultiPoint server。 在你允许用户登录到你的 MultiPoint 服务环境中的工作站之前，你应限制对服务器的访问。  
  
远程桌面用户组中的任何用户都可以登录到 MultiPoint server。 默认情况下，用户组是 "远程桌面用户" 组的成员，因此每个本地用户和域用户都可以登录到 MultiPoint 服务器。 若要限制对 MultiPoint 服务器的访问，请从 "远程桌面用户" 组中删除 "Everyone" 用户组，然后将特定用户或组添加到 "远程桌面用户" 组。  
  
## <a name="add-or-remove-users-or-groups-to-the-remote-desktop-users-group"></a>在远程桌面用户组中添加或删除用户或组  
  
1.  从 "**开始**" 屏幕打开 "**计算机管理**"。  
  
2.  在控制台树中的 "**本地用户和组**" 下，单击 "**组**"。  
  
3.  双击 "**远程桌面用户**"，然后按照说明添加或删除用户。  
  
    -   若要限制对服务器的一般访问权限，请删除 Everyone 组。  
  
    -   若要为 MultiPoint server 用户授予访问工作站的权限，请将每个本地帐户或每个域用户或组帐户添加到远程桌面用户组中。  