---
title: PowerShell_ise
description: PowerShell_ise 命令的参考文章，用于启动 Windows PowerShell 集成脚本环境 (ISE) 会话。
ms.topic: article
ms.assetid: 32c41b5b-a210-47d9-bd8c-91eb9830b4f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f82779d122d3fedf3dac7ecf51b6da0601373421
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884872"
---
# <a name="powershell_ise"></a>PowerShell_ise

Windows PowerShell 集成脚本环境 (ISE) 是一种图形化主机应用程序，可用于读取、写入、运行、调试和测试图形辅助环境中的脚本和模块。 智能感知、显示命令、代码段、tab 自动补全、语法着色、可视调试和上下文相关帮助等主要功能提供丰富的脚本编写体验。

## <a name="using-powershellexe"></a>使用 PowerShell.exe

**PowerShell_ISE.exe**工具启动 Windows PowerShell ISE 会话。 使用**PowerShell_ISE.exe**时，可以使用其可选参数打开 Windows PowerShell ISE 中的文件，或启动没有配置文件或多线程单元的 Windows PowerShell ISE 会话。

- 若要在命令提示符窗口、Windows PowerShell 或 "**开始**" 菜单中启动 Windows PowerShell ISE 会话，请键入：

  ```powershell
  PowerShell_Ise.exe
  ```

- 若要打开脚本 ( ps1) 、script module () 、 (、XML 文件或) 中任何其他受支持的文件，请键入：

  ```powershell
  PowerShell_Ise.exe <filepath>
  ```

  在 Windows PowerShell 3.0 中，可以使用可选**文件**参数，如下所示：

  ```powershell
  PowerShell_Ise.exe -file <filepath>
  ```

- 若要在不使用 Windows PowerShell 配置文件的情况下启动 Windows PowerShell ISE 会话，请使用**NoProfile**参数。  (在 Windows PowerShell 3.0 ) 中引入了**NoProfile**参数，请键入：

  ```powershell
  PowerShell_Ise.exe -NoProfile
  ```

- 若要查看 PowerShell_ISE.exe 帮助文件，请键入：

    ```powershell
    PowerShell_Ise.exe -help
    PowerShell_Ise.exe -?
    PowerShell_Ise.exe /?
    ```

### <a name="remarks"></a>备注

- 有关**PowerShell_ISE.exe**命令行参数的完整列表，请参阅[about_PowerShell_Ise.Exe](/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe)。

- 有关启动 Windows PowerShell 的其他方法的信息，请参阅[启动 Windows powershell](/powershell/scripting/windows-powershell/starting-windows-powershell)。

- Windows PowerShell 在 Windows Server 操作系统的服务器核心安装选项上运行。 但是，因为 Windows PowerShell ISE 需要图形用户界面，所以它不在服务器核心安装上运行。

## <a name="additional-references"></a>其他参考

- [about_PowerShell_Ise.exe](/powershell/module/microsoft.powershell.core/about/about_powershell_exe)
