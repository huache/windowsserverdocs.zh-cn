---
title: wscript
description: Wscript.echo 的参考文章，其中提供了一个环境，用户可以在其中使用各种对象模型执行任务来执行脚本。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2fbaf193-cdbd-414c-84c9-bb5720f84c29
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 08/21/2018
ms.openlocfilehash: bfa92f7e80bbf89fac615a3cd6ddf7057c0d6a4c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936070"
---
# <a name="wscript"></a>wscript



Windows 脚本宿主提供了一个环境，用户可以在其中使用各种不同的语言执行脚本，这些语言使用各种对象模型来执行任务。

## <a name="syntax"></a>语法

```
wscript [<scriptname>] [/b] [/d] [/e:<engine>] [{/h:cscript|/h:wscript}] [/i] [/job:<identifier>] [{/logo|/nologo}] [/s] [/t:<number>] [/x] [/?] [<ScriptArguments>]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|scriptname|指定脚本文件的路径和文件名。|
|/b|指定批处理模式，该模式不会显示警报、脚本错误或输入提示。 这与 **/i**相反。|
|/d|启动调试器。|
|/e|指定用于运行脚本的引擎。 这使你可以运行使用自定义文件扩展名的脚本。 如果没有/e 参数，则只能运行使用已注册文件扩展名的脚本。 例如，如果您尝试运行以下命令：<br>```cscript test.admin```<br>你将收到以下错误消息： "输入错误：没有适用于文件扩展名的脚本引擎"。<br>使用非标准文件扩展名的一个优点是它可以防止意外双击脚本并运行你确实不想运行的内容。 <br>这不会在 admin 文件扩展名和 VBScript 之间创建永久关联。 每次运行使用 admin 文件扩展名的脚本时，都需要使用/e 参数。|
|/h： cscript|将**cscript.exe**注册为运行脚本的默认脚本主机。|
|/h： wscript.echo|将**wscript.exe**注册为运行脚本的默认脚本主机。 当省略 **/h**选项时，这是默认值。|
|/i|指定交互模式，显示警报、脚本错误和输入提示。</br>这是默认值，**反之亦然。**|
|/作业\<identifier>|运行 **.wsf**脚本文件中由*标识符*标识的作业。|
|/logo|指定在运行脚本之前 Windows 脚本宿主横幅显示在控制台中。</br>这是默认值，与 **/nologo**相反。|
|/nologo|指定在运行脚本之前不显示 Windows 脚本宿主横幅。 这与 **/logo**相反。|
|/s|为当前用户保存当前的命令提示符选项。|
|/t:\<number>|指定脚本可运行的最长时间（秒）。 最多可指定32767秒。</br>默认值为无时间限制。|
|/x|启动调试器中的脚本。|
|ScriptArguments|指定传递给脚本的参数。 每个脚本参数必须以斜杠（/）开头。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   执行该任务无需具有管理凭据。 因此，作为安全方面的最佳做法，请考虑以不具有管理凭据的用户身份执行该任务。
-   若要打开命令提示符，请在“开始”**** 屏幕上，键入 **cmd**，然后单击“命令提示符”****。
-   每个参数都是可选的;但是，如果不指定脚本，则不能指定脚本参数。 如果未指定脚本或任何脚本参数， **wscript.exe**将显示 " **Windows 脚本宿主设置**" 对话框，您可以使用该对话框为**wscript.exe**在本地计算机上运行的所有脚本设置全局脚本属性。
-   **/T**参数通过设置计时器防止脚本运行过多。 当时间超过指定值时， **wscript.echo**将中断脚本引擎并结束进程。
-   Windows 脚本文件通常具有以下文件扩展名之一： **. .wsf**、 **.vbs**、 **.js**。
-   如果双击扩展名没有关联的脚本文件，将显示 "**打开方式**" 对话框。 选择 " **wscript.echo** " 或 " **cscript**"，然后选择 "**始终使用此程序打开此文件类型**"。 这会将**wscript.exe**或**cscript.exe**作为此文件类型的文件的默认脚本宿主来注册。
-   您可以为各个脚本设置属性。 有关详细信息，请参阅[Windows 脚本主机概述](https://technet.microsoft.com/library/cc738350(v=ws.10).aspx)。
-   Windows 脚本宿主可以使用 **.wsf**脚本文件。 每个 **.wsf**文件都可以使用多个脚本引擎，并执行多个作业。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
