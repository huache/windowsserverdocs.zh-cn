---
title: msiexec
description: Msiexec 命令的参考文章，它提供了从命令行对 Windows Installer 执行安装、修改和执行操作的方法。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 122eb0ce-ecbc-4909-a52a-15c3413619af
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aacdc55ac3895efad7dd9499ea1402b538fb8a9b
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934960"
---
# <a name="msiexec"></a>msiexec

提供从命令行对 Windows Installer 进行安装、修改和执行操作的方法。

## <a name="install-options"></a>安装选项

设置用于启动安装包的安装类型。

### <a name="syntax"></a>语法

```
msiexec.exe [/i][/a][/j{u|m|/g|/t}][/x] <path_to_package>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| /i | 指定正常安装。 |
| /a | 指定管理安装。 |
| /ju | 将产品播发到当前用户。 |
| /jm | 将产品播发到所有用户。 |
| /j/g | 指定播发包使用的语言标识符。 |
| /j/t | 将转换应用于播发包。 |
| /x | 卸载包。 |
| `<path_to_package>` | 指定安装包文件的位置和名称。 |

#### <a name="examples"></a>示例

若要使用正常的安装过程从 C：驱动器安装名为*example.msi*的包，请键入：

```
msiexec.exe /i "C:\example.msi"
```

## <a name="display-options"></a>显示选项

你可以根据目标环境配置用户在安装过程中看到的内容。 例如，如果要将包分发到所有客户端进行手动安装，则应使用完整的 UI。 但是，如果要使用组策略部署包，而不需要用户交互，则不应涉及到 UI。

### <a name="syntax"></a>语法

```
msiexec.exe /i <path_to_package> [/quiet][/passive][/q{n|b|r|f}]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| `<path_to_package>` | 指定安装包文件的位置和名称。 |
| /quiet | 指定静默模式，这意味着不需要用户交互。 |
| /passive | 指定无人参与模式，这意味着安装仅显示进度栏。 |
| /qn | 指定在安装过程中没有 UI。 |
| /qn + | 指定在安装过程中没有 UI，最终对话框除外。 |
| /qb | 指定在安装过程中有一个基本 UI。 |
| /qb + | 指定在安装过程中有一个基本 UI，其中包含最终对话框。 |
| /qr | 指定在安装过程中减少的 UI 体验。 |
| /qf | 指定在安装过程中的完整 UI 体验。 |

##### <a name="remarks"></a>备注

- 如果用户取消了安装，则不会显示模式框。 可以使用**qb +！** 或**qb！ +** 隐藏 "**取消**" 按钮。

#### <a name="examples"></a>示例

若要使用普通安装过程和无 UI 安装包*C:\example.msi*，请键入：

```
msiexec.exe /i "C:\example.msi" /qn
```

## <a name="restart-options"></a>重新启动选项

如果安装包覆盖了文件或尝试更改正在使用的文件，则可能需要重新启动才能完成安装。

### <a name="syntax"></a>语法

```
msiexec.exe /i <path_to_package> [/norestart][/promptrestart][/forcerestart]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| `<path_to_package>` | 指定安装包文件的位置和名称。 |
| /norestart | 安装完成后，停止设备重新启动。 |
| /promptrestart | 如果需要重新启动，则会提示用户。 |
| /forcerestart | 安装完成后，重新启动设备。 |

#### <a name="examples"></a>示例

若要安装包*C:\example.msi*，请在结束时使用不重启的正常安装过程，键入：

```
msiexec.exe /i "C:\example.msi" /norestart
```

## <a name="logging-options"></a>日志记录选项

如果需要调试安装包，可以将参数设置为创建包含特定信息的日志文件。

### <a name="syntax"></a>语法

```
msiexec.exe [/i][/x] <path_to_package> [/L{i|w|e|a|r|u|c|m|o|p|v|x+|!|*}] <path_to_log>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| /i | 指定正常安装。 |
| /x | 卸载包。 |
| `<path_to_package>` | 指定安装包文件的位置和名称。 |
| /li | 启用日志记录，并在输出日志文件中包含状态消息。 |
| /lw | 启用日志记录，并在输出日志文件中包含非致命警告。 |
| /le | 启用日志记录，并在输出日志文件中包含所有错误消息。 |
| /la | 启用日志记录，并包括有关在输出日志文件中启动操作时的信息。 |
| /lr | 启用日志记录，并在输出日志文件中包含特定于操作的记录。 |
| /lu | 启用日志记录，并在输出日志文件中包含用户请求信息。 |
| /lc | 启用日志记录，并在输出日志文件中包含初始 UI 参数。 |
| /lm | 启用日志记录，并在输出日志文件中包含内存不足或严重退出信息。 |
| /lo | 启用日志记录，并在输出日志文件中包含磁盘空间不足的消息。 |
| /lp | 启用日志记录，并在输出日志文件中包含终端属性。 |
| /lp | 启用日志记录，并在输出日志文件中包含终端属性。 |
| /lv | 启用日志记录，并在输出日志文件中包含详细输出。 |
| /lp | 启用日志记录，并在输出日志文件中包含终端属性。 |
| /lx | 启用日志记录，并在输出日志文件中包含额外的调试信息。 |
| /l + | 启用日志记录，并将信息追加到现有日志文件。 |
| /l! | 启用日志记录并刷新日志文件中的每一行。 |
| /l | 启用日志记录并记录所有信息，包括详细信息（**/lv**）或额外的调试信息（**/lx**）。 |
| `<path_to_logfile>` | 指定输出日志文件的位置和名称。 |

#### <a name="examples"></a>示例

若要安装 package *C:\example.msi*，请使用具有所提供的所有日志记录信息的正常安装过程，包括详细输出，并将输出日志文件存储在*C:\package.log*中，键入：

```
msiexec.exe /i "C:\example.msi" /L*V "C:\package.log"
```

## <a name="update-options"></a>更新选项

您可以应用或删除使用安装包的更新。

### <a name="syntax"></a>语法

```
msiexec.exe [/p][/update][/uninstall[/package<product_code_of_package>]] <path_to_package>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| /p | 安装修补程序。 如果要以无提示方式安装，还必须将 REINSTALLMODE 属性设置为*ecmus* ，并将其重新安装为*ALL*。 否则，修补程序仅更新在目标设备上缓存的 MSI。 |
| /update | 安装修补程序选项。 如果要应用多个更新，则必须使用分号（;) 分隔它们。 |
| /package | 安装或配置产品。 |

#### <a name="examples"></a>示例

```
msiexec.exe /p "C:\MyPatch.msp"
msiexec.exe /p "C:\MyPatch.msp" /qb REINSTALLMODE="ecmus" REINSTALL="ALL"
msiexec.exe /update "C:\MyPatch.msp"
```

```
msiexec.exe /uninstall {1BCBF52C-CD1B-454D-AEF7-852F73967318} /package {AAD3D77A-7476-469F-ADF4-04424124E91D}
```

其中，第一个 GUID 是修补程序 GUID，第二个 GUID 是应用修补程序的 MSI 产品代码。

## <a name="repair-options"></a>修复选项

可以使用此命令修复已安装的包。

### <a name="syntax"></a>语法

```
msiexec.exe [/f{p|o|e|d|c|a|u|m|s|v}] <product_code>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| /fp | 如果文件丢失，则修复包。 |
| /fo | 如果文件丢失或安装了较早的版本，则修复包。 |
| /fe | 如果文件丢失或安装了相等或更低的版本，则修复包。 |
| /fd | 如果文件丢失或安装了不同的版本，则修复包。 |
| /fc | 如果文件丢失或校验和与计算的值不匹配，则修复包。 |
| /fa | 强制重新安装所有文件。 |
| /fu | 修复所有必需的特定于用户的注册表项。 |
| /fm | 修复所有必需的特定于计算机的注册表项。 |
| /fs | 修复所有现有的快捷方式。 |
| /fc | 从源运行并重新缓存本地包。 |

#### <a name="examples"></a>示例

若要强制根据要修复的 MSI 产品代码重新安装所有*文件，请*键入：

```
msiexec.exe /fa {AAD3D77A-7476-469F-ADF4-04424124E91D}
```

## <a name="set-public-properties"></a>设置公共属性

可以通过此命令设置公共属性。 有关可用属性及其设置方法的信息，请参阅[公共属性](https://docs.microsoft.com/windows/win32/msi/public-properties)。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Msiexec.exe 命令行选项](https://docs.microsoft.com/windows/win32/msi/command-line-options)

- [标准安装程序命令行选项](https://docs.microsoft.com/windows/win32/msi/standard-installer-command-line-options)
