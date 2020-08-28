---
title: fsutil
description: Fsutil 命令的参考文章，它执行与文件分配表 (FAT) 和 NTFS 文件系统相关的任务。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: 2e748187-6a10-4bb0-aed5-34f886a250d2
ms.topic: reference
ms.date: 08/21/2018
ms.openlocfilehash: d8ad17d65d2f16a16393e71b707bcd6478de0052
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037765"
---
# <a name="fsutil"></a>fsutil

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8，Windows Server 2008 R2，Windows 7

执行与文件分配表 (FAT) 和 NTFS 文件系统相关的任务，例如管理重新分析点、管理稀疏文件或卸除卷。 如果在没有参数的情况下使用，则 **fsutil** 将显示受支持的子命令的列表。

> [!NOTE]
> 您必须以管理员或 Administrators 组成员的身份登录才能使用 **fsutil**。 此命令非常强大，只应由全面了解 Windows 操作系统的高级用户使用。
>
>必须先启用适用于 Linux 的 Windows 子系统，然后才能运行 **fsutil**。 以管理员身份在 PowerShell 中运行以下命令以启用此可选功能：
>
> `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`
>
> 安装后，系统将提示您重新启动计算机。 计算机重启后，你将能够以管理员身份运行 **Fsutil** 。

### <a name="parameters"></a>参数

| 子命令 | 说明 |
| ---------- | ----------- |
| [fsutil 8dot3name](fsutil-8dot3name.md) | 例如，查询或更改系统上的短名称行为的设置会生成8.3 个字符长度的文件名。 删除目录中的所有文件的短名称。 如果从目录中的文件中去除短名称，则扫描目录并标识可能会受到影响的注册表项。 |
| [fsutil dirty](fsutil-dirty.md) | 查询卷的未更新位是否已设置或是否设置卷的未更新位。 如果设置了卷的未更新位，则在下次重新启动计算机时， **autochk** 会自动检查卷中是否存在错误。 |
| [fsutil file](fsutil-file.md) | 按用户名查找文件 (如果启用了磁盘配额) ，查询为文件分配的范围，设置文件的短名称，设置文件的有效数据长度，为文件设置零数据，创建指定大小的新文件，在给定的情况下查找文件 ID，或者查找指定文件 ID 的文件链接名称。 |
| [fsutil fsinfo](fsutil-fsinfo.md) | 列出所有驱动器并查询驱动器类型、卷信息、特定于 NTFS 的卷信息或文件系统统计信息。 |
| [fsutil hardlink](fsutil-hardlink.md) | 列出文件的硬链接，或创建 (文件) 目录条目的硬链接。 每个文件都可以被视为至少具有一个硬链接。 在 NTFS 卷上，每个文件都可以有多个硬链接，因此单个文件可以出现在多个目录中 (甚至在同一目录中，名称) 不同。 由于所有链接都引用同一个文件，因此程序可以打开任何链接，并修改该文件。 只有在删除文件的所有链接后，才会从文件系统中删除该文件。 创建硬链接后，程序可以像使用任何其他文件名一样使用它。 |
| [fsutil objectid](fsutil-objectid.md) | 管理对象标识符，Windows 操作系统使用这些标识符跟踪对象（如文件和目录）。 |
| [fsutil quota](fsutil-quota.md) | 管理 NTFS 卷上的磁盘配额，以便更精确地控制基于网络的存储。 磁盘配额以每个卷为基础实现，并且启用基于每个用户的软存储限制。 |
| [fsutil repair](fsutil-repair.md) | 查询或设置卷的自愈状态。 自愈 NTFS 尝试在不需要运行 **Chkdsk.exe** 的情况下联机更正 ntfs 文件系统损坏。 包括启动磁盘上的验证并等待修复完成。 |
| [fsutil reparsepoint](fsutil-reparsepoint.md) | 查询或删除 (NTFS 文件系统对象的重新分析点，这些对象具有包含用户控制的数据) 的可定义属性。 重新分析点用于在 i/o) 子系统 (扩展输入/输出中的功能。 它们用于目录交接点和卷装入点。 文件系统筛选器驱动程序也使用它们将特定文件标记为特定于该驱动程序。 |
| [fsutil resource](fsutil-resource.md) | 创建辅助事务资源管理器，启动或停止事务资源管理器，显示有关事务资源管理器或修改其行为的信息。 |
| [fsutil sparse](fsutil-sparse.md) | 管理稀疏文件。 稀疏文件是一个文件，其中包含一个或多个未分配的数据区域。 程序会将这些未分配的区域视为包含值为零的字节，但不会使用磁盘空间来表示这些零。 所有有意义或非零的数据都将被分配，而所有无意义的数据 (由零组成的大型数据字符串) 不会被分配。 读取稀疏文件时，分配的数据按存储的方式返回，未分配的数据将作为零返回 (默认情况下，根据 C2 安全要求规范) 。 稀疏文件支持允许将数据从文件中的任何位置解除分配。 |
| [fsutil tiering](fsutil-tiering.md) | 启用存储层功能的管理，例如设置和禁用层标志和列表。 |
| [fsutil transaction](fsutil-transaction.md)   | 提交指定的事务，回滚指定的事务，或者显示有关该事务的信息。 |
| [fsutil usn](fsutil-usn.md) | 管理 (USN) 更改日志的更新序列号，该日志提供对卷上的文件进行的所有更改的持久日志。 |
| [fsutil volume](fsutil-volume.md) | 管理卷。 卸载卷，查询以查看磁盘上可用空间量，或查找正在使用指定群集的文件。 |
| [fsutil wim](fsutil-wim.md) | 提供用于发现和管理支持 WIM 的文件的函数。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)