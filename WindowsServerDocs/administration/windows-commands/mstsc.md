---
title: mstsc
description: Mstsc 命令的参考主题，用于创建到远程桌面会话主机服务器或其他远程计算机的连接，编辑现有远程桌面连接（.rdp）配置文件，以及将使用客户端连接管理器创建的旧连接文件迁移到新的 .rdp 连接文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 59801227-1e7e-4dbd-96e6-f54102a3ce92
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a6620cc2f954e43a6e68369f9b1f3480c1fc508c
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354347"
---
# <a name="mstsc"></a>mstsc

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建与远程桌面会话主机服务器或其他远程计算机的连接，编辑现有远程桌面连接（.rdp）配置文件，并将使用客户端连接管理器创建的旧连接文件迁移到新的 .rdp 连接文件。

## <a name="syntax"></a>语法

```
mstsc.exe [<connectionfile>] [/v:<server>[:<port>]] [/admin] [/f] [/w:<width> /h:<height>] [/public] [/span]
mstsc.exe /edit <connectionfile>
mstsc.exe /migrate
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ------------|
| `<connectionfile>` | 指定用于连接的 .rdp 文件的名称。 |
| /v:`<server>[:<port>]` | 指定远程计算机，还可以选择要连接到的端口号。 |
| /admin | 将你连接到用于管理服务器的会话。 |
| /f | 以全屏模式启动远程桌面连接。 |
| /w`<width>` | 指定远程桌面窗口的宽度。 |
| /h`<height>` | 指定远程桌面窗口的高度。 |
| /public | 在公用模式下运行远程桌面。 在公用模式下，不会缓存密码和位图。 |
| /span | 使远程桌面的宽度和高度与本地虚拟桌面相匹配，如有必要，跨越多个监视器。 |
| /edit`<connectionfile>` | 打开指定的 .rdp 文件以进行编辑。 |
| /migrate | 将通过客户端连接管理器创建的旧连接文件迁移到新的 .rdp 连接文件。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 默认情况下，将为每个用户在用户的**Documents**文件夹中存储为隐藏文件。

- 用户创建的 .rdp 文件默认保存在用户的**Documents**文件夹中，但可以保存在任何位置。

- 若要跨越多台监视器，监视器必须使用相同的分辨率，并且必须水平对齐（即并排）。 目前不支持跨越在客户端系统上垂直放置的多台监视器。

### <a name="examples"></a>示例

若要以全屏模式连接到会话，请键入：

```
mstsc /f
```

若要打开一个名为 *.rdp*的文件进行编辑，请键入：

```
mstsc /edit filename.rdp
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
