---
title: Windows Server 的 windows Defender 概述
description: Windows Server 安全
ms.prod: windows-server
ms.technology: security-windows-defender
ms.topic: article
ms.assetid: 751efb33-a08e-4e90-9208-6f2bc319e029
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 0eb88a0ad80de1060971b6de5e0c5ba313ce0fad
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80855060"
---
# <a name="windows-defender-antivirus-for-windows-server"></a>适用于 Windows Server 的 windows Defender 防病毒

>适用于：Windows Server 2016

Windows Server 2016 现在包含 Windows Defender 防病毒。 Windows Defender AV 是一种恶意软件防护，可立即主动保护 Windows Server 2016 免受已知的恶意软件的攻击，并且可以通过 Windows 更新定期更新反恶意软件定义。

有关详细信息，请参阅 windows 10 文档库[中的 Windows Defender 防病毒](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10)。


尽管 Windows 10 和 Windows Server 2016 上的 Windows Defender AV 在功能、配置和管理方面大体相同，但仍有一些关键区别：

- 在 Windows Server 2016 中，会基于定义的服务器角色应用[自动排除项](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/configure-server-exclusions-windows-defender-antivirus)。
- 在 Windows Server 2016 中，如果运行其他防病毒产品，Windows Defender AV 将无法禁用自己。

Windows [server 2016 上的 Windows Defender 防病毒](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016)主题包含特定于 windows server 2016 的设置和配置信息，包括如何执行以下操作：

-   [启用接口](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_UsingDef)

-   [验证 Windows Defender AV 是否正在运行]( https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefRun)

-   [更新反恶意软件定义]( https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_UpdateDef)

-   [提交示例]( https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefSamples)

-   [配置自动排除]( https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefExclusions)
