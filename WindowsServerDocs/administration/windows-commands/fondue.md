---
title: 干酪
description: Fondue 命令的参考文章，可通过从 Windows 更新或组策略指定的其他源下载所需文件来启用 Windows 可选功能。
ms.topic: reference
ms.assetid: fc4467f6-ddbb-4d6d-b51e-5a50a957b8c0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c80c6b1aef9ea37bdb4ff497ff7a7b5e54f8c468
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634846"
---
# <a name="fondue"></a>干酪

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过从 Windows 更新或组策略指定的其他源下载所需的文件来启用 Windows 可选功能。 此功能的清单文件必须已安装在 Windows 映像中。

## <a name="syntax"></a>语法

```
fondue.exe /enable-feature:<feature_name> [/caller-name:<program_name>] [/hide-ux:{all | rebootrequest}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /enable-feature`<feature_name>` | 指定要启用的 Windows 可选功能的名称。 每个命令行只能启用一项功能。 若要启用多个功能，请使用每个功能的 fondue.exe。 |
| /caller-name:`<program_name>` | 指定从脚本或批处理文件中调用 fondue.exe 时的程序或进程的名称。 如果出现错误，则可以使用此选项将程序名称添加到 SQM 报表中。 |
| /hide-ux:`{all | rebootrequest}` | 使用 " **全部** " 可向用户隐藏所有消息，包括访问 Windows 更新的进度和权限请求。 如果权限是必需的，则操作将失败。<p>使用 **rebootrequest** 仅隐藏要求重新启动计算机的权限的用户消息。 如果你有控制重新启动请求的脚本，请使用此选项。 |

### <a name="examples"></a>示例

若要启用 Microsoft .NET Framework 4.8，请键入：

```
fondue.exe /enable-feature:NETFX4
```

若要启用 Microsoft .NET Framework 4.8，请将程序名称添加到 SQM 报表，而不向用户显示消息，请键入：

```
fondue.exe /enable-feature:NETFX4 /caller-name:Admin.bat /hide-ux:all
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Microsoft .NET Framework 4.8 下载](https://dotnet.microsoft.com/download/dotnet-framework/net48)
