---
title: cscript
description: 用于启动脚本以便在命令行环境中运行的 cscript 命令的参考文章。
ms.topic: reference
ms.assetid: fba3cbca-594e-4663-bb22-4ee0f63a1ac6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2e35efeccc219a7e678e2eccab74de5d0c4d6837
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628993"
---
# <a name="cscript"></a>cscript

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

开始要在命令行环境中运行的脚本。

>[!IMPORTANT]
> 执行该任务无需具有管理凭据。 因此，作为安全方面的最佳做法，请考虑以不具有管理凭据的用户身份执行该任务。

## <a name="syntax"></a>语法

```
cscript <scriptname.extension> [/b] [/d] [/e:<engine>] [{/h:cscript | /h:wscript}] [/i] [/job:<identifier>] [{/logo | /nologo}] [/s] [/t:<seconds>] [x] [/u] [/?] [<scriptarguments>]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| scriptname | 指定具有可选文件扩展名的脚本文件的路径和文件名。 |
| /b | 指定批处理模式，该模式不会显示警报、脚本错误或输入提示。 |
| /d | 启动调试器。 |
| /e:`<engine>` | 指定用于运行脚本的引擎。 |
| /h： cscript | 将 cscript.exe 注册为运行脚本的默认脚本主机。 |
| /h： wscript.echo | 将 wscript.exe 注册为运行脚本的默认脚本主机。 这是默认设置。 |
| /i | 指定交互模式，显示警报、脚本错误和输入提示。 这是默认值，与相反 `/b` 。 |
| /作业<identifier> | 运行 .wsf 脚本文件中由 *标识符* 标识的作业。 |
| /logo | 指定在运行脚本之前 Windows 脚本宿主横幅显示在控制台中。 这是默认值，与相反 `/nologo` 。 |
| /nologo | 指定在运行脚本之前不显示 Windows 脚本宿主横幅。 |
| /s | 保存当前用户的当前命令提示符选项。 |
| /t:<seconds> | 指定脚本可在几秒)  (运行的最长时间。 最多可指定32767秒。 默认值为无时间限制。 |
| /U | 为从控制台重定向的输入和输出指定 Unicode。 |
| /x | 启动调试器中的脚本。 |
| /? | 显示可用的命令参数，并提供使用它们的帮助。 这与键入无参数 **cscript.exe** ，而不是脚本。 |
| scriptarguments | 指定传递给脚本的参数。 每个脚本参数前面必须有一个斜杠 (**/**) 。 |

#### <a name="remarks"></a>备注

- 每个参数都是可选的;但是，如果不指定脚本，则不能指定脚本参数。 如果未指定脚本或任何脚本参数，cscript.exe 将显示 cscript.exe 语法和有效的主机选项。

- **/T**参数通过设置计时器防止脚本运行过多。 当运行时间超过指定值时，cscript 将中断脚本引擎并结束进程。

- Windows 脚本文件通常具有以下文件扩展名之一：. .wsf、.vbs、.js。 Windows 脚本宿主可以使用 .wsf 脚本文件。 每个 .wsf 文件都可以使用多个脚本引擎，并执行多个作业。

- 如果双击扩展名没有关联的脚本文件，将显示 " **打开方式** " 对话框。 选择 "wscript.echo" 或 "cscript"，然后选择 " **始终使用此程序打开此文件类型**"。 这会将 wscript.exe 或 cscript 注册为此文件类型文件的默认脚本主机。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
