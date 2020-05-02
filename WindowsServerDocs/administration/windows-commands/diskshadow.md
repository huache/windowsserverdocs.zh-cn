---
title: diskshadow
description: Diskshadow 的参考主题，它是一个公开卷影复制服务（VSS）提供的功能的工具。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e962537d-b759-4368-b6f1-e8391cf7b221
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: db1b1602bcbde41c2d92af925ff819ef390220e1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719425"
---
# <a name="diskshadow"></a>diskshadow

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

diskshadow 是公开卷影复制服务（VSS）提供的功能的工具。 默认情况下，diskshadow 使用与 diskraid 或 DiskPart 类似的交互式命令解释器。 diskshadow 还包括可编写脚本的模式。  
  
> [!NOTE]  
> 本地 Administrators 组中的成员身份或等效身份是运行 diskshadow 所需的最低要求。  
  

## <a name="syntax"></a>语法  
对于交互模式，请在命令提示符下键入以下命令，以启动 diskshadow 命令解释器：  
  
```  
diskshadow  
```  
  
对于脚本模式，请键入以下内容，其中*script*是包含 diskshadow 命令的脚本文件：  
  
```  
diskshadow -s script.txt  
```  
  
### <a name="parameters"></a>参数  
可以在 diskshadow 命令解释器或通过脚本文件运行以下命令：  
  
|参数|描述|  
|-------|--------|  
|[set_2](set_2.md)|设置用于创建卷影副本的上下文、选项、详细模式和元数据文件。|  
|[模拟还原](simulate-restore.md)|测试编写器参与计算机上的还原会话，而不向编写器发出**PreRestore**或**PostRestore**事件。|  
|[加载元数据](load-metadata.md)|在导入可传送的卷影副本之前加载元数据 .cab 文件，或者在还原时加载写入器元数据。|  
|[编写器](writer.md)|验证是否包括了写入器或组件，或者是否从备份或还原过程中排除了写入器或组件。|  
|[add](add.md)|将卷添加到要进行卷影复制的卷集中，或将别名添加到别名环境。|  
|[create_1](create_1.md)|使用当前上下文和选项设置启动卷影复制创建过程。|  
|[exec](exec.md)|在本地计算机上执行文件。|  
|[开始备份](begin-backup.md)|启动完整备份会话。|  
|[结束备份](end-backup.md)|结束完整备份会话，并根据需要发出具有相应编写器状态的**Backupcomplete**事件。|  
|[开始还原](begin-restore.md)|启动还原会话并向相关编写器发出**PreRestore**事件。|  
|[结束还原](end-restore.md)|结束还原会话并向相关编写器发出**PostRestore**事件。|  
|[reset](reset.md)|将 diskshadow 重置为默认状态。|  
|[list](list.md)|列出系统上的编写器、卷影副本或当前注册的卷影复制提供程序。|  
|[删除阴影](delete-shadows.md)|删除卷影副本。|  
|[import](import.md)|将已加载的元数据文件中的可传送影子副本导入到系统中。|  
|[掩码](mask.md)|删除使用**import**命令导入的硬件卷影副本。|  
|[让](expose.md)|将永久性卷影副本作为驱动器号、共享或装入点公开。|  
|[隐藏](unexpose.md)|unexposes 使用**公开**命令公开的卷影副本。|  
|[break_2](break_2.md)|将卷影副本卷与 VSS 解除。|  
|[回到](revert.md)|将卷恢复到指定的卷影副本。|  
|[exit_1](exit_1.md)|退出 diskshadow。|  
  
## <a name="remarks"></a>备注  
  
-   创建卷影副本至少需要 "**添加**" 和 "**创建**"。 但是，这将使上下文和选项设置，将为副本备份，并且将仅创建不带备份执行脚本的卷影副本。  
  
## <a name="examples"></a>示例  
这是将创建卷影副本以进行备份的命令的示例序列。 可以将其另存为 dsh 文件，并以 diskshadow \/s 脚本执行。 dsh  
  
假设以下内容：  
  
-   你有一个名为 c：\\diskshadowdata 的现有目录。  
  
-   系统卷为 C：，数据卷为 d：  
  
-   你在 c：\\diskshadowdata 中有一个 backupscript 文件。  
  
-   你的 backupscript 文件将执行卷影数据 p：和 q：的副本到你的备份驱动器。  
  
可以手动输入这些命令，也可以编写脚本：  
  
```  
#diskshadow script file  
set context persistent nowriters  
set metadata c:\diskshadowdata\example.cab  
set verbose on  
begin backup  
add volume c: alias Systemvolumeshadow  
add volume d: alias Datavolumeshadow  
  
create  
  
expose %Systemvolumeshadow% p:  
expose %Datavolumeshadow% q:  
exec c:\diskshadowdata\backupscript.cmd  
end backup  
#End of script  
```  
  
## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
  

