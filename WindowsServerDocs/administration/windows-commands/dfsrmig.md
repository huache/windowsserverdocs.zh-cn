---
title: dfsrmig
description: Dfsrmig 命令的参考文章，用于将 SYSvol 复制从 FRS 迁移到 DFS 复制，提供有关迁移进度的信息，并修改 AD DS 对象以支持迁移。
ms.topic: reference
ms.assetid: e1b6a464-6a93-4e66-9969-04f175226d8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a619a4f94f9b0afb0a855017de0283c763948698
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030205"
---
# <a name="dfsrmig"></a>dfsrmig

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

DFS 复制服务 dfsrmig.exe 的迁移工具随 DFS 复制服务一起安装。 此工具将 SYSvol 复制从文件复制服务迁移到 (FRS) 以分布式文件系统 (DFS) 复制。 它还提供有关迁移进度的信息并修改 Active Directory 域服务 (AD DS) 对象以支持迁移。

## <a name="syntax"></a>语法

```
dfsrmig [/setglobalstate <state> | /getglobalstate | /getmigrationstate | /createglobalobjects |
/deleterontfrsmember [<read_only_domain_controller_name>] | /deleterodfsrmember [<read_only_domain_controller_name>] | /?]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `/setglobalstate <state>` | 将域的全局迁移状态设置为与 *状态*指定的值相对应的状态。 只能将全局迁移状态设置为稳定状态。 *状态值*包括：<ul><li>**0** -开始状态</li><li>**1** -准备状态</li><li>**2** -重定向状态</li><li>**3** -消除状态</li></ul> |
| /getglobalstate | 在 PDC 模拟器上运行时，从 AD DS 数据库的本地副本中检索域的当前全局迁移状态。 使用此选项可确认设置了正确的全局迁移状态。<p>**重要提示：** 只应在 PDC 模拟器上运行此命令。 |
| /getmigrationstate | 检索域中所有域控制器的当前本地迁移状态，并确定这些本地状态是否与当前全局迁移状态匹配。 使用此选项确定所有域控制器是否已达到全局迁移状态。 |
| /createglobalobjects | 在 DFS 复制使用的 AD DS 中创建全局对象和设置。 使用此选项手动创建对象和设置的唯一情况是：<ul><li>**迁移期间会升级新的只读域控制器**。 如果在将新的只读域控制器转换为已 **准备好** 的状态后将其升级到域中，但在迁移到 **消除** 状态之前，不会创建与新域控制器对应的对象，从而导致复制和迁移失败。</li><li>**DFS 复制服务的全局设置缺失或已被删除**。 如果域控制器缺少这些设置，则从 **开始** 状态到 **准备** 状态的迁移将停止，以 **准备** 转换状态。 **注意：** 由于只读域控制器的 DFS 复制服务的全局 AD DS 设置是在 PDC 模拟器上创建的，因此，在只读域控制器上的 DFS 复制服务可以使用这些设置之前，这些设置需要从 PDC 仿真器复制到只读域控制器。 由于 Active Directory 复制延迟，此复制可能需要一段时间。 |
| `/deleterontfrsmember [<read_only_domain_controller_name>]` | 如果没有为指定值，则将删除与指定的只读域控制器对应的 FRS 复制的全局 AD DS 设置，或删除所有只读域控制器的 FRS 复制的全局 AD DS 设置 `<read_only_domain_controller_name>` 。<p>不需要在正常的迁移过程中使用此选项，因为在从 **重定向** 状态到已 **消除** 状态的迁移过程中，DFS 复制服务会自动删除这些 AD DS 设置。 使用此选项，仅当在只读域控制器上自动删除失败时，并且在从 **重定向** 状态到已 **消除** 状态的迁移过程中停止了长 ime 的只读域控制器时，才能手动删除 AD DS 设置。 |
| `/deleterodfsrmember [<read_only_domain_controller_name>]` | 删除与指定的只读域控制器对应的 DFS 复制的全局 AD DS 设置，或者，如果没有为指定值，则删除所有只读域控制器的 DFS 复制的全局 AD DS 设置 `<read_only_domain_controller_name>` 。<p>使用此选项，仅当在只读域控制器上自动删除失败时，并且在将迁移从已准备状态回滚到启动状态时，会长时间停止只读域控制器时，才手动删除 AD DS 设置。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 使用 `/setglobalstate <state>` 命令在 PDC 模拟器上 AD DS 中设置全局迁移状态，以启动和控制迁移过程。 如果 PDC 模拟器不可用，则此命令将失败。

- 迁移到已 **消除** 状态的操作是不可逆的，不可能进行回滚，因此，仅当你完全提交使用 DFS 复制进行 SYSvol 复制时，才将值 **3** 用于 *状态* 。

- 全局迁移状态必须是稳定的迁移状态。

- Active Directory 复制将全局状态复制到域中的其他域控制器，但由于复制延迟，如果 `dfsrmig /getglobalstate` 在除 PDC 模拟器以外的域控制器上运行，则可能会出现不一致的情况。

- 的输出 `dsfrmig /getmigrationstate` 指示迁移到当前全局状态是否完成，并列出尚未达到当前全局迁移状态的任何域控制器的本地迁移状态。 域控制器的本地迁移状态还可以包括尚未达到当前全局迁移状态的域控制器的转换状态。

- 只读域控制器无法从 AD DS 删除设置，PDC 模拟器执行此操作，更改最终会在 active directory 复制适用延迟后复制到只读域控制器。

- 仅在 Windows Server 域功能级别运行的域控制器上支持 **dfsrmig** 命令，因为从 FRS 到 DFS 复制的 SYSvol 迁移仅适用于在该级别运行的域控制器。

- 你可以在任何域控制器上运行 **dfsrmig** 命令，但创建或操作 AD DS 对象的操作仅允许读写功能的域控制器 (不在只读域控制器) 上。

## <a name="examples"></a>示例

若要将全局迁移状态设置为 "准备 (**1**) 并启动迁移或从准备好的状态回滚，请键入：

```
dfsrmig /setglobalstate 1
```

若要将全局迁移状态设置为开始 (**0**) 并启动回退到开始状态，请键入：

```
dfsrmig /setglobalstate 0
```

若要显示全局迁移状态，请键入：

```
dfsrmig /getglobalstate
```

`dfsrmig /getglobalstate`命令输出：

```
Current DFSR global state: Prepared
Succeeded.
```

若要显示有关所有域控制器上的本地迁移状态是否匹配全局迁移状态的信息，以及本地状态与全局状态不匹配的任何本地迁移状态，请键入：

```
dfsrmig /GetMigrationState
```

`dfsrmig /getmigrationstate`当所有域控制器上的本地迁移状态与全局迁移状态匹配时，从命令输出：

```
All Domain Controllers have migrated successfully to Global state (Prepared).
Migration has reached a consistent state on all Domain Controllers.
Succeeded.
```

`dfsrmig /getmigrationstate`当某些域控制器上的本地迁移状态与全局迁移状态不匹配时，从命令输出。

```
The following Domain Controllers are not in sync with Global state (Prepared):
Domain Controller (Local Migration State) DC type
=========
CONTOSO-DC2 (start) ReadOnly DC
CONTOSO-DC3 (Preparing) Writable DC
Migration has not yet reached a consistent state on all domain controllers
State information might be stale due to AD latency.
```

若要创建 DFS 复制在迁移过程中不会自动创建这些设置的域控制器 AD DS 中使用的全局对象和设置，请键入：

```
dfsrmig /createglobalobjects
```

若要删除名为 contoso-dc2 的只读域控制器的 FRS 复制的全局 AD DS 设置，请在迁移过程中键入以下内容：

```
dfsrmig /deleterontfrsmember contoso-dc2
```

若要删除所有只读域控制器的 FRS 复制的全局 AD DS 设置（如果迁移过程未自动删除这些设置），请键入：

```
dfsrmig /deleterontfrsmember
```

若要删除名为 contoso-dc2 的只读域控制器 DFS 复制的全局 AD DS 设置，如果迁移过程未自动删除这些设置，请键入：

```
dfsrmig /deleterodfsrmember contoso-dc2
```

若要删除所有只读域控制器的全局 AD DS DFS 复制设置（如果迁移过程未自动删除这些设置），请键入：

```
dfsrmig /deleterodfsrmember
```

若要在命令提示符下显示帮助：

```
dfsrmig
```

```
dfsrmig /?
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](https://go.microsoft.com/fwlink/?LinkId=122056)

- [SYSvol 迁移系列：第2部分 dfsrmig.exe： SYSvol 迁移工具](https://techcommunity.microsoft.com/t5/storage-at-microsoft/sysvol-migration-series-part-2-8211-dfsrmig-exe-the-sysvol/ba-p/423470)

- [Active Directory 域服务](../../identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview.md)
