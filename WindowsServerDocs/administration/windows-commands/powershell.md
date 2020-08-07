---
title: PowerShell
description: PowerShell 命令的参考文章，可从命令提示符中打开 PowerShell 控制台。
ms.topic: article
ms.assetid: 694fc970-0b6c-4046-b1b5-7eb1a0d26609
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 8608f10ae96d6137ce2dd7983d78236775af0df0
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884882"
---
# <a name="powershell"></a>PowerShell

Windows PowerShell 是一种基于任务的命令行 shell 和脚本语言，专为系统管理而设计。 在 .NET Framework 的基础上构建的 Windows PowerShell 可帮助 IT 专业人士和高级用户控制和自动执行 Windows 操作系统以及在 Windows 上运行的应用程序的管理。

## <a name="using-powershellexe"></a>使用 PowerShell.exe

**PowerShell.exe**命令行工具在命令提示符窗口中启动 Windows PowerShell 会话。 使用**PowerShell.exe**时，可以使用其可选参数自定义会话。 例如，可以启动使用特定执行策略或排除 Windows PowerShell 配置文件的会话。 否则，该会话与 Windows PowerShell 控制台中启动的任何会话相同。

- 若要在命令提示符窗口中启动 Windows PowerShell 会话，请键入 `PowerShell` 。 将**PS**前缀添加到命令提示符，以指示你处于 Windows PowerShell 会话中。

- 若要使用特定执行策略启动会话，请使用**set-executionpolicy**参数，并键入：

    ```powershell
    PowerShell.exe -ExecutionPolicy Restricted
    ```

- 若要启动 Windows PowerShell 会话而不使用 Windows PowerShell 配置文件，请使用**NoProfile**参数，并键入：

    ```powershell
    PowerShell.exe -NoProfile
    ```

- 若要启动会话，请使用**set-executionpolicy**参数，并键入：

    ```powershell
    PowerShell.exe -ExecutionPolicy Restricted
    ```

- 若要查看 PowerShell.exe 帮助文件，请键入：

    ```powershell
    PowerShell.exe -help
    PowerShell.exe -?
    PowerShell.exe /?
    ```

- 若要在命令提示符窗口中结束 Windows PowerShell 会话，请键入 `exit` 。 典型的命令提示符返回。

### <a name="remarks"></a>备注

- 有关**PowerShell.exe**命令行参数的完整列表，请参阅[about_PowerShell.Exe](/powershell/module/microsoft.powershell.core/about/about_powershell_exe)。

- 有关启动 Windows PowerShell 的其他方法的信息，请参阅[启动 Windows powershell](/powershell/scripting/windows-powershell/starting-windows-powershell)。

- Windows PowerShell 在 Windows Server 操作系统的服务器核心安装选项上运行。 但是，需要图形用户界面的功能（如[Windows PowerShell 集成脚本环境 (ISE) ](/previous-versions//hh849182(v=technet.10))，以及[Out](/powershell/module/microsoft.powershell.utility/out-gridview)和[Show-Command](/powershell/module/microsoft.powershell.utility/show-command) cmdlet）不在服务器核心安装上运行。

## <a name="additional-references"></a>其他参考

- [about_PowerShell.Exe](/powershell/module/microsoft.powershell.core/about/about_powershell_exe)

- [about_PowerShell_Ise.exe](/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe)

- [Windows PowerShell](/powershell/)
