---
title: bdehdcfg
description: Bdehdcfg 命令的参考文章，该命令使用 BitLocker 驱动器加密所需的分区来准备硬盘驱动器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4c92cd74-188e-4fec-b7c4-fe4e8903e032
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0a8b926459f2d1fb96b9a48910c163eb9aaab02c
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85923358"
---
# <a name="bdehdcfg"></a>bdehdcfg

使用 BitLocker 驱动器加密所需的分区准备硬盘驱动器。 大多数 Windows 7 安装都不需要使用此工具，因为 BitLocker 安装程序包括根据需要准备和重新分区驱动器。

> [!WARNING]
> 在**计算机配置 \ 管理模板 \Windows 组件 \Bitlocker 驱动器加密 \ 数据驱动器**中，出现与 "**拒绝对不受 BitLocker 保护的固定驱动器的写访问**" 组策略设置的已知冲突。
>
>如果启用此策略设置时在计算机上运行 bdehdcfg，则可能会遇到以下问题：
>
>- 如果尝试收缩驱动器并创建系统驱动器，则驱动器大小将会成功减少，并将创建一个原始分区。 但是，将不会格式化原始分区。 显示以下错误消息：无法对新的活动驱动器进行格式化。 你可能需要手动准备你的 BitLocker 驱动器。
>
>- 如果尝试使用未分配空间创建系统驱动器，则将创建一个原始分区。 但是，将不会格式化原始分区。 显示以下错误消息：无法对新的活动驱动器进行格式化。 你可能需要手动准备你的 BitLocker 驱动器。
>
>- 如果尝试将现有驱动器合并到系统驱动器中，则该工具将无法将所需的启动文件复制到目标驱动器上以创建系统驱动器。 显示以下错误消息： BitLocker 安装程序未能复制启动文件。 你可能需要手动准备你的 BitLocker 驱动器。
>
>- 如果要强制实施此策略设置，则无法重新分区硬盘驱动器，因为驱动器受到保护。 如果要从以前版本的 Windows 升级组织中的计算机，并且这些计算机配置了单个分区，则应在将策略设置应用到计算机之前创建所需的 BitLocker 系统分区。

## <a name="syntax"></a>语法

```
bdehdcfg [–driveinfo <drive_letter>] [-target {default|unallocated|<drive_letter> shrink|<drive_letter> merge}] [–newdriveletter] [–size <size_in_mb>] [-quiet]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |----------- |
| [bdehdcfg： system.io.driveinfo](bdehdcfg-driveinfo.md) | 显示指定驱动器上的驱动器号、总大小、最大可用空间和分区特征。 仅列出了有效的分区。 如果已存在四个主分区或扩展分区，则不会列出未分配的空间。 |
| [bdehdcfg：目标](bdehdcfg-target.md) | 定义要用作系统驱动器的驱动器部分，并使该部分处于活动状态。 |
| [bdehdcfg： newdriveletter](bdehdcfg-newdriveletter.md) | 将新的驱动器号分配给用作系统驱动器的驱动器部分。 |
| [bdehdcfg： size](bdehdcfg-size.md) | 确定在创建新的系统驱动器时系统分区的大小。 |
| [bdehdcfg： quiet](bdehdcfg-quiet.md) | 禁止显示命令行界面中的所有操作和错误，并指示 bdehdcfg 使用 "是" 答案到在后续驱动器准备过程中可能出现的任何 "是/否" 提示。 |
| [bdehdcfg：重新启动](bdehdcfg-restart.md) | 指示在驱动器准备完成后重新启动计算机。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
