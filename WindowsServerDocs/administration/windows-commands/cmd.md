---
title: cmd
description: Cmd 命令的参考文章，它启动命令解释器 Cmd.exe 的新实例。
ms.topic: article
ms.assetid: 6ec588db-31a9-4a73-a970-65a2c6f4abbe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0c4e651a4f88ffa1d85d5be225b3ae6e5d1676dd
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880089"
---
# <a name="cmd"></a>cmd

启动命令解释器 Cmd.exe 的新实例。 如果不使用参数， **cmd**将显示操作系统的版本和版权信息。

## <a name="syntax"></a>语法

```
cmd [/c|/k] [/s] [/q] [/d] [/a|/u] [/t:{<b><f> | <f>}] [/e:{on | off}] [/f:{on | off}] [/v:{on | off}] [<string>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| /c | 执行*字符串*指定的命令，然后停止。 |
| 遇到 | 执行*string*指定的命令，然后继续。 |
| /s | 修改 **/c**或 **/k**之后的*字符串*处理。 |
| /q | 关闭 echo。 |
| /d | 禁止执行自动运行命令。 |
| /a | 将内部命令输出的格式设置为管道或文件， (ANSI) 美国国家标准学会。 |
| /U | 将内部命令输出的格式设置为作为 Unicode 的管道或文件。 |
| /t： {`<b><f>` | `<f>`} | 设置背景 (*b*) 和前景 (*f*) 颜色。 |
| /e：开启 | 启用命令扩展。 |
| /e： off | 禁用命令扩展。 |
| /f：开启 | 启用文件和目录名称完成。 |
| /f： off | 禁用文件和目录名称完成。 |
| /v：开启 | 启用延迟环境变量扩展。 |
| /v：关 | 禁用延迟的环境变量扩展。 |
| `<string>` | 指定要执行的命令。 |
| /? | 在命令提示符下显示帮助。 |

下表列出了可用作和的值的有效十六进制数字 `<b>` `<f>` ：

| 值 | Color |
| ----- | ----- |
| 0 | 黑色 |
| 1 | 蓝色 |
| 2 | 绿色 |
| 3 | Aqua |
| 4 | Red |
| 5 | 紫色 |
| 6 | Yellow |
| 7 | 白色 |
| 8 | 灰色 |
| 9 | 浅蓝色 |
| a | 浅绿 |
| b | 浅浅绿色 |
| c | 浅红色 |
| d | 浅紫色 |
| e | 浅黄色 |
| F | 亮白色 |

## <a name="remarks"></a>备注

- 若要使用的多个命令 `<string>` ，请用命令分隔符分隔它们， **&&** 并将它们括在引号中。 例如：

    ```
    "<command1>&&<command2>&&<command3>"
    ```

- 如果指定 **/c**或 **/k**，则只有在满足以下所有条件时， **cmd**进程、*字符串*的其余部分和引号才会保留：

    - 你还不使用 **/s**。

    - 只使用一组引号。

    - 不使用引号内的任何特殊字符 (例如：  & < >  ( ) @ ^ |) 。

    - 在引号内使用一个或多个空白字符。

    - 引号中的*字符串*是可执行文件的名称。

    如果未满足上述条件，则将通过检查第一个字符来处理*字符串*，以验证它是否是左引号。 如果第一个字符是左引号，则将其与右引号一起去除。 保留右引号后面的任何文本。

- 如果未指定 **/d** in *string*，Cmd.exe 将查找以下注册表子项：

    - **HKEY_LOCAL_MACHINE \Software\Microsoft\Command Processor\AutoRun\ REG_SZ**

    - **HKEY_CURRENT_USER \Software\Microsoft\Command Processor\AutoRun\ REG_EXPAND_SZ**

    如果存在一个或两个注册表子项，它们将在所有其他变量之前执行。

    > [!CAUTION]
    > 不正确地编辑注册表可能会对系统造成严重损坏。 在更改注册表之前，应备份计算机上任何有价值的数据。

- 您可以使用 **/e： off**禁用特定进程的命令扩展。 您可以通过设置以下**REG_DWORD**值为计算机或用户会话上的所有**cmd**命令行选项启用或禁用扩展：

    - **HKEY_LOCAL_MACHINE \Software\Microsoft\Command Processor\EnableExtensions\ REG_DWORD**

    - **HKEY_CURRENT_USER \Software\Microsoft\Command Processor\EnableExtensions\ REG_DWORD**

    使用) ，将**REG_DWORD**值设置为启用了**0 × 1** () 或**0 × 0** (禁用注册表中的 Regedit.exe。 用户指定的设置优先于计算机设置，命令行选项优先于注册表设置。

    > [!CAUTION]
    > 不正确地编辑注册表可能会对系统造成严重损坏。 在更改注册表之前，应备份计算机上任何有价值的数据。

    启用命令扩展时，会影响以下命令：
    - **assoc**

    - **call**

    - **chdir (cd) **

    - **color**

    - **del (erase) **

    - **endlocal**

    - **for**

    - **ftype**

    - **goto**

    - **if**

    - **mkdir (md) **

    - **popd**

    - **prompt**

    - **pushd**

    - **set**

    - **setlocal**

    - **shift**

    - **开始** (还包括对外部命令进程的更改) 

- 如果启用延迟环境变量扩展，则可以使用感叹号字符来替换运行时环境变量的值。

- 默认情况下，不启用文件和目录名称完成。 您可以使用 **/f：**{**on**off} 为**cmd**命令的特定进程启用或禁用文件名称完成  |  **off**。 您可以通过设置以下**REG_DWORD**值为计算机上的**cmd**命令或用户登录会话启用或禁用文件和目录名称完成：

    - **HKEY_LOCAL_MACHINE \Software\Microsoft\Command Processor\CompletionChar\ REG_DWORD**

    - **HKEY_LOCAL_MACHINE \Software\Microsoft\Command Processor\PathCompletionChar\ REG_DWORD**

    - **HKEY_CURRENT_USER \Software\Microsoft\Command Processor\CompletionChar\ REG_DWORD**

    - **HKEY_CURRENT_USER \Software\Microsoft\Command Processor\PathCompletionChar\ REG_DWORD**

    若要设置**REG_DWORD**值，请运行 Regedit.exe，并对特定函数使用控制字符的十六进制值 (例如， **0 × 9**为 TAB， **0 × 08**表示) 。 用户指定的设置优先于计算机设置，命令行选项优先于注册表设置。

    > [!CAUTION]
    > 不正确地编辑注册表可能会对系统造成严重损坏。 在更改注册表之前，应备份计算机上任何有价值的数据。

- 如果通过使用 **/f： on**启用文件和目录名完成，请使用**ctrl + D**来完成目录名称，并使用**ctrl + f**来完成文件名。 若要在注册表中禁用特定的完成字符，请使用空白 [**0 × 20**] 的值，因为它不是有效的控制字符。

  - 按**ctrl + D**或**ctrl + F**，处理文件和目录名称的完成。 如果不存在) ，这些键组合函数会将通配符追加到*字符串* (，生成一个匹配的路径列表，然后显示第一个匹配的路径。<p>如果路径都不匹配，则文件和目录名称完成功能将发出嘟嘟声，并且不会更改显示。 若要在匹配路径列表中移动，请重复按**ctrl + D**或**ctrl + F** 。 若要向后移动列表，请同时按**SHIFT**键和**ctrl + D**或**ctrl + F** 。 若要放弃已保存的匹配路径列表并生成新列表，请编辑*字符串*，然后按**ctrl + D**或**ctrl + F**。 如果在 " **ctrl + D** " 和 " **ctrl + F**" 之间切换，则会丢弃已保存的匹配路径列表，并生成一个新列表。 组合键**ctrl + d**和**ctrl + f**之间的唯一区别在于， **ctrl + d**只匹配目录名称， **ctrl + f**匹配文件和目录名称。 如果在任何内置目录命令 (即**CD**、 **MD**或**RD**) 上使用文件和目录名称完成，则将采用目录完成。

  - 如果用引号将引号括起来，则文件和目录名称完成会正确地处理包含空格或特殊字符的文件名。

  - 必须使用引号将以下特殊字符括起来：  & < >  [] {} ^ =;！ "+，" ~ [空格]。

  - 如果提供的信息包含空格，则必须用引号将文本括 (例如，"Computer Name" ) 。

  - 如果从*字符串*内处理文件和目录名完成，则会丢弃光标右侧*路径*的任何部分 (在*字符串*中处理完成的位置) 。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
