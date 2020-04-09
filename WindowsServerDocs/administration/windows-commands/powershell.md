---
title: PowerShell
description: 了解如何从命令提示符中打开 PowerShell 控制台。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 694fc970-0b6c-4046-b1b5-7eb1a0d26609
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 327ac844bec0e4c89ee1443c193aa628de038dea
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837400"
---
# <a name="powershell"></a>PowerShell

Windows PowerShell 是一种基于任务的命令行 shell 和脚本语言，专为系统管理而设计。 Windows PowerShell 构建在 .NET Framework 之上，可帮助 IT 专业人士和超级用户控制和自动化在 Windows 上运行的 Windows 操作系统和应用程序的管理。

**Ngen.exe**命令行工具在命令提示符窗口中启动 Windows PowerShell 会话。 使用**PowerShell**时，可以使用它的可选参数自定义会话。 例如，可以启动使用特定执行策略或排除 Windows PowerShell 配置文件的会话。 否则，该会话与 Windows PowerShell 控制台中启动的任何会话相同。

## <a name="using-powershellexe"></a>使用 ngen.exe

您可以使用**ngen.exe**命令行工具在命令提示符窗口中启动 Windows PowerShell 会话。

- 若要在命令提示符窗口中启动 Windows PowerShell 会话，请键入 `PowerShell`。 将**PS**前缀添加到命令提示符，以指示你处于 Windows PowerShell 会话中。

- 若要使用特定执行策略启动会话，请使用**set-executionpolicy**参数。

    ```
    PowerShell.exe -ExecutionPolicy Restricted
    ```

- 若要在不使用 Windows PowerShell 配置文件的情况下启动 Windows PowerShell 会话，请使用**NoProfile**参数。

    ```
    PowerShell.exe -NoProfile
    ```
  
- 若要启动会话，请使用**set-executionpolicy**参数。

    ```
    PowerShell.exe -ExecutionPolicy Restricted
    ```
  
- 若要查看 ngen.exe 帮助文件，请使用以下命令格式。  
    
    ```
    PowerShell.exe -help, -?, /?
    ```

- 若要在命令提示符窗口中结束 Windows PowerShell 会话，请键入 `exit`。 典型的命令提示符返回。

有关**ngen.exe**命令行参数的完整列表，请参阅[about_PowerShell](https://go.microsoft.com/fwlink/?LinkID=113439)。

## <a name="other-ways-to-start-windows-powershell"></a>启动 Windows PowerShell 的其他方法

有关启动 Windows PowerShell 的其他方法的信息，请参阅[启动 Windows powershell](https://go.microsoft.com/fwlink/?LinkID=135259)。

## <a name="remarks"></a>备注

Windows PowerShell 在 Windows Server 操作系统的服务器核心安装选项上运行。 但是，需要图形用户界面的功能（如[Windows PowerShell 集成脚本环境（ISE））](https://technet.microsoft.com/library/hh849182)和[Out](https://go.microsoft.com/fwlink/?LinkID=113364)和[Show Command](https://go.microsoft.com/fwlink/?LinkID=217448) cmdlet 不能在服务器核心安装上运行。

## <a name="additional-references"></a>其他参考

[About_PowerShell .exe](https://go.microsoft.com/fwlink/?LinkID=113439)
[About_PowerShell_Ise .Exe](https://go.microsoft.com/fwlink/?LinkId=256512)
[Windows Powershell](https://go.microsoft.com/fwlink/?LinkID=107116)
[通过 windows powershell 编写脚本的](https://technet.microsoft.com/scriptcenter/dd742419)另请参阅