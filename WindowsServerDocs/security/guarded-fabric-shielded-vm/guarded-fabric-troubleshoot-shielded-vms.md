---
title: 排查受防护的 Vm
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 10/3/2018
ms.openlocfilehash: c80663256a2e3404666b739c0a81cd06ec3caced
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856370"
---
# <a name="troubleshoot-shielded-vms"></a>排查受防护的 Vm

>适用于： Windows Server 2019、Windows Server （半年频道）、Windows Server 2016

从 Windows Server 版本1803开始，为完全防护的 Vm 重新启用了虚拟机连接（VMConnect）增强会话模式和 PS Direct。 虚拟化管理员仍需要 VM 来宾凭据才能访问 VM，但这使得主机的网络配置断开时，主机可以更轻松地对受防护的 VM 进行故障排除。

若要为受防护的 Vm 启用 VMConnect 和 PS Direct，只需将它们移动到运行 Windows Server 1803 或更高版本的 Hyper-v 主机。 将自动重新启用允许这些功能的虚拟设备。 如果受防护的 VM 移动到运行的主机和更早版本的 Windows Server，则将再次禁用 VMConnect 和 PS Direct。

对于担心托管商是否有权访问 VM 并希望返回到原始行为的安全敏感客户，应在来宾操作系统中禁用以下功能：

- 在 VM 中禁用 PowerShell 直接服务：

  ```powershell
  Stop-Service vmicvmsession
  Set-Service vmicvmsession -StartupType Disabled
  ```

- 仅当你的来宾操作系统至少是 Windows Server 2019 或 Windows 10 （版本1809）时，才可禁用 VMConnect 增强会话模式。 在 VM 中添加以下注册表项，以禁用 VMConnect 增强会话控制台连接：

  ```
  reg add "HKLM\Software\Microsoft\Virtual Machine\Guest" /v DisableEnhancedSessionConsoleConnection /t REG_DWORD /d 1
  ```
