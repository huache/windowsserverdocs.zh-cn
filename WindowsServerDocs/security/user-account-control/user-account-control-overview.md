---
title: 用户帐户控制概述
description: Windows Server 安全
ms.prod: windows-server
ms.technology: security-tpm
ms.topic: article
ms.assetid: 1b7a39cd-fc10-4408-befd-4b2c45806732
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 6b79d4317303257677c01e81a655942b7e5a82d3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856310"
---
# <a name="user-account-control-overview"></a>用户帐户控制概述
\(UAC\) 的用户帐户控制是 Microsoft 总体安全愿景的基本组件。  UAC 帮助减轻恶意程序所带来的影响。

## <a name="feature-description"></a><a name="BKMK_OVER"></a>功能描述
UAC 允许所有用户使用标准用户帐户登录到他们的计算机。 使用标准用户令牌启动的进程可能会使用授予标准用户的访问权限执行任务。 例如，Windows 资源管理器会自动继承标准用户级别权限。 此外，使用 Windows 资源管理器执行的任何程序 \(例如，通过 double\-单击应用程序快捷方式\) 也使用标准用户权限集运行。 许多应用程序（包括操作系统本身包含的应用程序）均设计为以这种方式正常运行。

其他应用程序（尤其是那些未特意设计安全设置的应用程序）通常需要额外的权限才能成功运行。 这些类型的程序称为旧版应用程序。 此外，在 Windows 防火墙等程序中安装新软件和对程序进行配置更改等操作所需的权限比标准用户帐户可用的权限更多。

当应用程序需要使用超过标准用户权限运行时，UAC 可以将其他用户组还原到该令牌。 这样，用户就可以对对计算机或设备进行系统级更改的程序进行显式控制。

## <a name="practical-applications"></a><a name="BKMK_APP"></a>实用应用程序
UAC 中的管理员批准模式有助于防止恶意程序无提示安装，而无需管理员的知识。 它还有助于防止意外的系统\-范围更改。 最后，它可用于强制执行更高级别的相容性，在此情况下，对于每个管理进程，管理员必须主动同意或提供凭据。



