---
title: Diskshadow
description: Diskshadow 命令的参考主题，它是一个公开卷影复制服务（VSS）提供的功能的工具。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e962537d-b759-4368-b6f1-e8391cf7b221
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ae3a4ba57d9c29375c560c300a4e4ead807184fc
ms.sourcegitcommit: aed942d11f1a361fc1d17553a4cf190a864d1268
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83235193"
---
# <a name="diskshadow"></a>Diskshadow

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

Diskshadow 是公开卷影复制服务（VSS）提供的功能的工具。 默认情况下，Diskshadow 使用与 Diskraid 或 Diskpart 类似的交互式命令解释器。 Diskshadow 还包括可编写脚本的模式。

> [!NOTE]
> 本地 Administrators 组中的成员身份或等效身份是运行 Diskshadow 所需的最低要求。

## <a name="syntax"></a>语法

对于交互模式，请在命令提示符下键入以下命令，以启动 Diskshadow 命令解释器：

```
diskshadow
```

对于脚本模式，请键入以下内容，其中*script*是包含 Diskshadow 命令的脚本文件：

```
diskshadow -s script.txt
```

### <a name="parameters"></a>参数

你可以在 Diskshadow 命令解释器或通过脚本文件运行以下命令。 创建卷影副本至少需要 "**添加**" 和 "**创建**"。 但是，这丧失上下文和选项设置，将是副本备份，并创建没有备份执行脚本的卷影副本。

| 命令 | 说明 |
| --------- | ----------- |
| [set 命令](set_2.md) | 设置用于创建卷影副本的上下文、选项、详细模式和元数据文件。 |
| [加载元数据命令](load-metadata.md) | 在导入可传送的卷影副本之前加载元数据 .cab 文件，或者在还原时加载写入器元数据。 |
| [编写器命令](writer.md) | 验证是否包括了写入器或组件，或者是否从备份或还原过程中排除了写入器或组件。 |
| [添加命令](add.md) | 将卷添加到要进行卷影复制的卷集中，或将别名添加到别名环境。 |
| [create 命令](create.md) | 使用当前上下文和选项设置启动卷影复制创建过程。 |
| [exec 命令](exec.md) | 在本地计算机上执行文件。 |
| [开始备份命令](begin-backup.md) | 启动完整备份会话。 |
| [结束备份命令](end-backup.md) | 结束完整备份会话，并根据需要发出具有相应编写器状态的**backupcomplete**事件。 |
| [开始 restore 命令](begin-restore.md) | 启动还原会话并向相关编写器发出**prerestore**事件。 |
| [结束还原命令](end-restore.md) | 结束还原会话并向相关编写器发出**postrestore**事件。 |
| [reset 命令](reset.md) | 将 Diskshadow 重置为默认状态。 |
| [list 命令](list.md) | 列出系统上的编写器、卷影副本或当前注册的卷影复制提供程序。 |
| [删除阴影命令](delete-shadows.md) | 删除卷影副本。 |
| [导入命令](import.md) | 将已加载的元数据文件中的可传送影子副本导入到系统中。 |
| [mask 命令](mask.md) | 删除使用**import**命令导入的硬件卷影副本。 |
| [公开命令](expose.md) | 将永久性卷影副本作为驱动器号、共享或装入点公开。 |
| [隐藏命令](unexpose.md) | Unexposes 使用**公开**命令公开的卷影副本。 |
| [break 命令](break_2.md) | 将卷影副本卷与 VSS 解除。 |
| [revert 命令](revert.md) | 将卷恢复到指定的卷影副本。 |
| [exit 命令](exit.md) | 退出命令解释器或脚本。 |

## <a name="examples"></a>示例

这是将创建卷影副本以进行备份的命令的示例序列。 可以将其另存为 dsh 文件，并使用执行 `diskshadow /s script.dsh` 。

假设以下内容：

- 你有一个名为 c： diskshadowdata 的现有目录 \\ 。

- 系统卷为 C：，数据卷为 d：

- 你在 c： diskshadowdata 中有一个 backupscript 文件 \\ 。

- 你的 backupscript 文件将执行卷影数据 p：和 q：的副本到你的备份驱动器。

可以手动输入这些命令，也可以编写脚本：

```
#Diskshadow script file
set context persistent nowriters
set metadata c:\diskshadowdata\example.cab
set verbose on
begin backup
add volume c: alias systemvolumeshadow
add volume d: alias datavolumeshadow

create

expose %systemvolumeshadow% p:
expose %datavolumeshadow% q:
exec c:\diskshadowdata\backupscript.cmd
end backup
#End of script
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
