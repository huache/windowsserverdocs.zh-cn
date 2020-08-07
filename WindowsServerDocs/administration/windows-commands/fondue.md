---
title: 干酪
description: Fondue 命令的参考文章，可通过从 Windows 更新或组策略指定的其他源下载所需文件来启用 Windows 可选功能。
ms.topic: article
ms.assetid: fc4467f6-ddbb-4d6d-b51e-5a50a957b8c0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 16660ed745c28f84d7911f9784fbeb19a5c03ae3
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890189"
---
# <a name="fondue"></a>干酪

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

通过从 Windows 更新或组策略指定的其他源下载所需的文件来启用 Windows 可选功能。 此功能的清单文件必须已安装在 Windows 映像中。

## <a name="syntax"></a>语法

```
fondue.exe /enable-feature:<feature_name> [/caller-name:<program_name>] [/hide-ux:{all | rebootrequest}]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| /enable-feature`<feature_name>` | 指定要启用的 Windows 可选功能的名称。 每个命令行只能启用一项功能。 若要启用多个功能，请使用每个功能的 fondue.exe。 |
| /caller-name:`<program_name>` | 指定从脚本或批处理文件中调用 fondue.exe 时的程序或进程的名称。 如果出现错误，则可以使用此选项将程序名称添加到 SQM 报表中。 |
| /hide-ux:`{all | rebootrequest}` | 使用 "**全部**" 可向用户隐藏所有消息，包括访问 Windows 更新的进度和权限请求。 如果权限是必需的，则操作将失败。<p>使用**rebootrequest**仅隐藏要求重新启动计算机的权限的用户消息。 如果你有控制重新启动请求的脚本，请使用此选项。 |

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
