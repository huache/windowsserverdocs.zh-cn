---
title: BranchCache Network Shell 和 Windows PowerShell 命令
description: 本主题提供有关 Windows Server 2016 中 BranchCache 的网络 Shell 和 Windows PowerShell 命令参考资源的链接
manager: brianlic
ms.topic: article
ms.assetid: a0726752-0a78-472b-9667-2f91636c1b3b
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 13c62fd1c21cce98e5de2f6cc16f0edb6ee06a99
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87993795"
---
# <a name="branchcache-network-shell-and-windows-powershell-commands"></a>BranchCache Network Shell 和 Windows PowerShell 命令

>适用于：Windows Server（半年频道）、Windows Server 2016

在 Windows Server 2016 中，可以使用 Windows PowerShell 或 (Netsh 的网络外壳) 命令配置和管理 BranchCache。

在 Windows 的未来版本中，Microsoft 可能删除 BranchCache 的 Netsh 功能。 如果你当前使用 netsh 配置和管理 BranchCache 以及其他网络技术，Microsoft 建议你转换为 Windows PowerShell。

Windows PowerShell 和 Netsh 命令参考处于以下位置中。 尽管这两个命令引用均已发布到 Windows Server 2016 之前的操作系统，但这些引用对于此操作系统是准确的。

-   [Windows Server 2008 R2 中的 BranchCache Netsh 命令](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd979561(v=ws.10))

-   [Windows PowerShell 中的 BranchCache Cmdlet](/powershell/module/branchcache/?view=win10-ps)

> [!TIP]
> 若要查看 Windows PowerShell 提示符下 BranchCache 的 Windows PowerShell 命令，请在 Windows PowerShell 提示符下键入 `Get-Command -Module BranchCache`，然后按 ENTER。