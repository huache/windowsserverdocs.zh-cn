---
title: Windows Server 的 windows Defender 概述
description: Windows Server 安全
ms.topic: article
ms.assetid: 751efb33-a08e-4e90-9208-6f2bc319e029
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: 4ed6a8f9fc9618156963bd2b3c51e4819d8adb36
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638644"
---
# <a name="windows-defender-antivirus-for-windows-server"></a>适用于 Windows Server 的 windows Defender 防病毒

>适用于：Windows Server 2016

Windows Server 2016 现在包含 Windows Defender 防病毒。 Windows Defender AV 是一种恶意软件防护，可立即主动保护 Windows Server 2016 免受已知的恶意软件的攻击，并且可以通过 Windows 更新定期更新反恶意软件定义。

有关详细信息，请参阅 windows 10 文档库 [中的 Windows Defender 防病毒](/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) 。


尽管 Windows 10 和 Windows Server 2016 上的 Windows Defender AV 在功能、配置和管理方面大体相同，但仍有一些关键区别：

- 在 Windows Server 2016 中，会基于定义的服务器角色应用[自动排除项](/windows/threat-protection/windows-defender-antivirus/configure-server-exclusions-windows-defender-antivirus)。
- 在 Windows Server 2016 中，如果运行其他防病毒产品，Windows Defender AV 将无法禁用自己。

Windows [server 2016 上的 Windows Defender 防病毒](/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016) 主题包含特定于 windows server 2016 的设置和配置信息，包括如何执行以下操作：

-   [启用接口](/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_UsingDef)

-   [验证 Windows Defender AV 是否正在运行]( /windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefRun)

-   [更新反恶意软件定义]( /windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_UpdateDef)

-   [提交示例]( /windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefSamples)

-   [配置自动排除项]( /windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefExclusions)