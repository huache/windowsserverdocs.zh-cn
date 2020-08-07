---
title: mqbkup
description: Mqbkup 命令的参考文章，可将 MSMQ 消息文件和注册表设置备份到存储设备，并还原以前存储的消息和设置。
ms.topic: article
ms.assetid: 7bdd41c4-75ef-455f-b241-1d64a4c7acf5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7eecb016efd039d87774c3fd869e746df1e60178
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87886304"
---
# <a name="mqbkup"></a>mqbkup

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将 MSMQ 消息文件和注册表设置备份到存储设备，并还原以前存储的消息和设置。

备份和还原操作都将停止本地 MSMQ 服务。 如果已预先启动 MSMQ 服务，则实用工具将在备份或还原操作结束时尝试重新启动 MSMQ 服务。 如果服务在运行此实用工具之前已停止，则不会尝试重新启动该服务。

使用 MSMQ 消息备份/还原实用程序之前，必须先关闭所有使用 MSMQ 的本地应用程序。

## <a name="syntax"></a>语法

```
mqbkup {/b | /r} <folder path_to_storage_device>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| ------- | -------- |
| /b | 指定备份操作。 |
| /r | 指定还原操作。 |
| `<folder path_to_storage_device>` | 指定存储 MSMQ 消息文件和注册表设置的路径。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果在执行备份或还原操作时指定的文件夹不存在，则该实用工具会自动创建文件夹。

- 如果选择指定现有文件夹，则该文件夹必须为空。 如果指定一个非空的文件夹，该实用工具将删除其中包含的每个文件和子文件夹。 在这种情况下，系统将提示你授予删除现有文件和子文件夹的权限。 您可以使用 **/y**参数指示您事先同意删除指定文件夹中的所有现有文件和子文件夹。

- 用于存储 MSMQ 消息文件的文件夹的位置存储在注册表中。 因此，实用工具会将 MSMQ 消息文件还原到注册表中指定的文件夹，而不是还原操作之前使用的存储文件夹。

### <a name="examples"></a>示例

若要备份所有 MSMQ 消息文件和注册表设置，并将它们存储在 C：驱动器上的*msmqbkup*文件夹中，请键入：

```
mqbkup /b c:\msmqbkup
```

若要删除 C：驱动器上*oldbkup*文件夹中的所有现有文件和子文件夹，然后在该文件夹中存储 MSMQ 消息文件和注册表设置，请键入：

```
mqbkup /b /y c:\oldbkup
```

若要还原 MSMQ 消息和注册表设置，请键入：

```
mqbkup /r c:\msmqbkup
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [MSMQ Powershell 参考](/powershell/module/msmq/?view=win10-ps)
