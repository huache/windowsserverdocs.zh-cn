---
title: PowerShell_ise
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 32c41b5b-a210-47d9-bd8c-91eb9830b4f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5fb143c3d365b47f66aee5c64bfdc7dc26e5794f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723283"
---
# <a name="powershell_ise"></a>PowerShell_ise



Windows PowerShell 集成脚本环境（ISE）是一种图形化主机应用程序，使你能够在图形辅助环境中读取、编写、运行、调试和测试脚本与模块。 智能感知、显示命令、代码段、tab 自动补全、语法着色、可视调试和上下文相关帮助等主要功能提供丰富的脚本编写体验。

**PowerShell_ISE**工具启动 Windows PowerShell ISE 会话。 当你使用**PowerShell_ISE**时，可以使用它的可选参数打开 Windows PowerShell ISE 中的文件，或启动没有配置文件或多线程单元的 Windows PowerShell ISE 会话。

Windows PowerShell 2.0 中引入了**PowerShell_ISE** ，并大大扩展了 windows powershell 3.0。

## <a name="using-powershell_iseexe"></a>使用 PowerShell_ISE

你可以使用**PowerShell_ISE**来启动和结束 Windows PowerShell 会话，如下所示：
- 若要启动 Windows PowerShell ISE 会话，请在命令提示符窗口中，在 Windows PowerShell 中，或在 "开始" 菜单中键入：  
  ```
  PowerShell_Ise
  ```  
- 若要在 Windows PowerShell ISE 中打开脚本（ps1）、脚本模块（. hbase-runner.psm1）、模块清单（psd1）、XML 文件或任何其他受支持的文件，请使用以下命令格式：  
  ```
  PowerShell_Ise <FilePath>
  ```  
  在 Windows PowerShell 3.0 中，可以使用可选**文件**参数，如下所示：  
  ```
  PowerShell_Ise -File <FilePath>
  ```  
- 若要在不使用 Windows PowerShell 配置文件的情况下启动 Windows PowerShell ISE 会话，请使用**NoProfile**参数。 （ **NoProfile**参数是在 Windows PowerShell 3.0 中引入的。）  
  ```
  PowerShell_Ise -NoProfile
  ```  
- 若要在命令提示符窗口中查看**PowerShell_ISE .Exe**帮助文件，请使用以下命令格式：  
  ```
  PowerShell_Ise -help, -?, /?
  ```  
  有关**PowerShell_ISE**命令行参数的完整列表，请参阅[about_PowerShell_Ise](https://go.microsoft.com/fwlink/?LinkId=256512)。

## <a name="start-windows-powershell-ise-in-other-ways"></a>以其他方式启动 Windows PowerShell ISE

有关启动 Windows PowerShell ISE 的其他方法的信息，请参阅[启动 Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=135259)。

## <a name="remarks"></a>备注

Windows PowerShell 在 Windows Server 操作系统的服务器核心安装选项上运行。 但是，因为 Windows PowerShell ISE 需要图形用户界面，所以它不在服务器核心安装上运行。

## <a name="additional-references"></a>其他参考

[about_PowerShell_Ise.exe](https://go.microsoft.com/fwlink/?LinkId=256512)
[通过 windows powershell](https://technet.microsoft.com/scriptcenter/dd742419) about_PowerShell_Ise .exe[about_PowerShell](https://go.microsoft.com/fwlink/?LinkID=113439)
[Windows powershell](https://go.microsoft.com/fwlink/?LinkID=107116)
脚本的另请参阅