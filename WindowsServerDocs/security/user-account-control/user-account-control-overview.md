---
title: 用户帐户控制概述
description: Windows Server 安全
ms.topic: article
ms.assetid: 1b7a39cd-fc10-4408-befd-4b2c45806732
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: 2729bafe910db6814479464a007ce0e49f8b3205
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638859"
---
# <a name="user-account-control-overview"></a>用户帐户控制概述
用户帐户控制 \( UAC \) 是 Microsoft 总体安全愿景的基本组件。  UAC 帮助减轻恶意程序所带来的影响。

## <a name="feature-description"></a><a name="BKMK_OVER"></a>功能说明
UAC 允许所有用户使用标准用户帐户登录到他们的计算机。 使用标准用户令牌启动的进程可能会使用授予标准用户的访问权限执行任务。 例如，Windows 资源管理器会自动继承标准用户级别权限。 此外，使用 Windows 资源管理器执行的任何程序（ \( 例如，通过双击 \- 应用程序快捷方式）， \) 也可以使用标准的用户权限集来运行。 许多应用程序（包括操作系统本身包含的应用程序）均设计为以这种方式正常运行。

其他应用程序（尤其是那些未特意设计安全设置的应用程序）通常需要额外的权限才能成功运行。 这些类型的程序称为旧版应用程序。 此外，在 Windows 防火墙等程序中安装新软件和对程序进行配置更改等操作所需的权限比标准用户帐户可用的权限更多。

当应用程序需要使用超过标准用户权限运行时，UAC 可以将其他用户组还原到该令牌。 这样，用户就可以对对计算机或设备进行系统级更改的程序进行显式控制。

## <a name="practical-applications"></a><a name="BKMK_APP"></a>实际的应用程序
UAC 中的管理员批准模式有助于防止恶意程序无提示安装，而无需管理员的知识。 它还有助于防止意外的系统 \- 范围更改。 最后，它可以用于强制执行更高级别的合规性，其中管理员必须主动同意或为每个管理进程提供凭据。



