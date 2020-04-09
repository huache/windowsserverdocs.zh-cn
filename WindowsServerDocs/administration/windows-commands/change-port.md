---
title: change port
description: "\"更改端口\" 的 Windows 命令主题，它列出或更改 COM 端口映射，使其与 MS-DOS 应用程序兼容。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3d772c90-e849-4e74-b9ec-b6cae1159336 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 39273382038edb7709f2d99baea8090d71df3a57
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848070"
---
# <a name="change-port"></a>change port

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

列出或更改要与 MS-DOS 应用程序兼容的 COM 端口映射。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

> [!NOTE]
> 在 Windows Server 2008 R2 中，“终端服务”被重命名为“远程桌面服务”。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。

## <a name="syntax"></a>语法

```
change port [<PortX>=<PortY| /d <PortX| /query]
```

### <a name="parameters"></a>参数


|    参数    |              说明               |
|-----------------|----------------------------------------|
| <PortX>=<PortY> | 将 COM <*PortX*> 映射到 <*PortY*> |
|   /d <PortX>    | 删除 COM <*PortX*的映射> |
|     /query      | 显示当前端口映射 |
|       /?        | 在命令提示符下显示帮助 |

## <a name="remarks"></a>备注

- 大多数 MS-DOS 应用程序仅支持 COM1 到 COM4 串行端口。 "**更改端口**" 命令将串行端口映射到不同的端口号，这允许不支持高编号 COM 端口的应用程序访问串行端口。 重新映射仅适用于当前会话，如果从会话中注销然后重新登录，则不会保留。

- 使用不带任何参数的**change 端口**显示可用 COM 端口及其当前映射。

## <a name="examples"></a><a name=BKMK_examples></a>示例

- 若要将 COM12 映射到 COM1 以供基于 MS-DOS 的应用程序使用，请键入：
  ```
  change port com12=com1
  ```
- 若要显示当前端口映射，请键入：
  ```
  change port /query
  ```

### <a name="additional-references"></a>其他参考
- - [命令行语法项](command-line-syntax-key.md)
- [change](change.md)
- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
