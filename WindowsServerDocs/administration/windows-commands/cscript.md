---
title: cscript
description: Cscript 的参考主题，用于启动脚本以便在命令行环境中运行。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fba3cbca-594e-4663-bb22-4ee0f63a1ac6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 758fa87806d530c79ae8de02985e4ca1f75747d9
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716818"
---
# <a name="cscript"></a>cscript

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

启动脚本，使其在命令行环境中运行。

## <a name="syntax"></a>语法
```
cscript <Scriptname.extension> [/B] [/D] [/E:<Engine>] [{/H:cscript|/H:wscript}] [/I] [/Job:<Identifier>] [{/Logo|/NoLogo}] [/S] [/T:<Seconds>] [/X] [/U] [/?] [<ScriptArguments>]
```
#### <a name="parameters"></a>参数

|      参数       |                                                                      描述                                                                       |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Scriptname |                                 指定具有可选文件扩展名的脚本文件的路径和文件名。                                 |
|          /B          |                                指定批处理模式，该模式不会显示警报、脚本错误或输入提示。                                |
|          /D          |                                                                  启动调试器。                                                                  |
|     电邮<Engine>      |                                                  指定用于运行脚本的引擎。                                                  |
|      /H： cscript      |                                         将 cscript.exe 注册为运行脚本的默认脚本宿主。                                          |
|      /H： wscript.echo      |                               将 wscript.echo 注册为运行脚本的默认脚本主机。 这是默认设置。                               |
|          /I          |        指定交互模式，显示警报、脚本错误和输入提示。 这是默认值，**反之亦然。**         |
|  任务<Identifier>   |                                             运行 .wsf 脚本文件中由*标识符*标识的作业。                                             |
|        /Logo         | 指定在运行脚本之前 Windows 脚本宿主横幅显示在控制台中。 这是默认值，与 **/nologo**相反。 |
|       /Nologo        |                                 指定在运行脚本之前不显示 Windows 脚本宿主横幅。                                 |
|          /S          |                                             保存当前用户的当前命令提示符选项。                                             |
|     关心<Seconds>     |            指定脚本可运行的最长时间（秒）。 最多可指定32767秒。 默认值为无时间限制。             |
|          /U          |                                      为从控制台重定向的输入和输出指定 Unicode。                                       |
|          /X          |                                                           启动调试器中的脚本。                                                           |
|          /?          |  显示可用的命令参数，并提供使用它们的帮助。 这与键入不带参数的**cscript.exe**和无脚本相同。  |
|   ScriptArguments    |                        指定传递给脚本的参数。 每个脚本参数必须以斜杠（**/**）开头。                         |

### <a name="remarks"></a>备注
-   执行该任务无需具有管理凭据。 因此，作为安全方面的最佳做法，请考虑以不具有管理凭据的用户身份执行该任务。
-   若要打开命令提示符，请在 "**开始**" 屏幕上键入**cmd**，然后单击 "**命令提示符**"。
-   每个参数都是可选的;但是，如果不指定脚本，则不能指定脚本参数。 如果未指定脚本或任何脚本参数，则 cscript.exe 将显示 cscript.exe 语法和有效的主机选项。
-   **/T**参数通过设置计时器防止脚本运行过多。 当运行时间超过指定值时，cscript 将中断脚本引擎并结束进程。
-   Windows 脚本文件通常具有以下文件扩展名之一：. .wsf、.vbs、.js。
-   您可以为各个脚本设置属性。 有关详细信息，请参阅“相关主题”。
-   Windows 脚本宿主可以使用 .wsf 脚本文件。 每个 .wsf 文件都可以使用多个脚本引擎，并执行多个作业。
-   如果双击扩展名没有关联的脚本文件，将显示 "**打开方式**" 对话框。 选择 "wscript.echo" 或 "cscript"，然后选择 "**始终使用此程序打开此文件类型**"。 这会将 wscript.echo 或 cscript 注册为此文件类型文件的默认脚本主机。
-   您可以为各个脚本设置属性。
-   Windows 脚本宿主可以使用 .wsf 脚本文件。 每个 .wsf 文件都可以使用多个脚本引擎，并执行多个作业。

####  <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
