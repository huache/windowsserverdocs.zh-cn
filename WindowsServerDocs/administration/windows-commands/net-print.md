---
title: net print
description: Net print 命令的参考文章。 此命令已弃用，并且在将来的 Windows 版本中不保证其受支持。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f59b2015-4698-415d-9a74-09566c466f40
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: af02ca14156c8a85ee54700983e2af6807752f91
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85934818"
---
# <a name="net-print"></a>net print

> [!IMPORTANT]
> 此命令已弃用。 但是，可以使用[prnjobs 命令](prnjobs.md)、 [Windows Management Instrumentation （WMI）](https://docs.microsoft.com/windows/win32/wmisdk/wmi-start-page)、 [PRINTMANAGEMENT.MSC in Powershell](https://docs.microsoft.com/powershell/module/printmanagement)或[面向 IT 专业人员的脚本资源](https://gallery.technet.microsoft.com/ScriptCenter/site/search?f%5B0%5D.Type=RootCategory&f%5B0%5D.Value=printing&f%5B0%5D.Text=Printing)来执行许多相同的任务。

显示有关指定打印机队列或指定的打印作业的信息，或控制指定的打印作业。

## <a name="syntax"></a>语法

```
net print {\\<computername>\<sharename> | \\<computername> <jobnumber> [/hold | /release | /delete]} [help]
```

### <a name="parameters"></a>parameters

| 参数 | 说明 |
| ---------- | ----------- |
| `\\<computername>\<sharename>` | 按名称指定要显示其信息的计算机和打印队列。 |
| `\\<computername>` | 指定（按名称）承载要控制的打印作业的计算机。 如果未指定计算机，则假定为本地计算机。 需要 `<jobnumber>` 参数。 |
| `<jobnumber>` | 指定要控制的打印作业的编号。 此编号由承载打印作业的打印队列的计算机分配。 计算机将编号分配给打印作业后，该数字不会分配给该计算机所承载的任何队列中的任何其他打印作业。 使用参数时是必需的 `\\<computername>` 。 |
| `[/hold | /release | /delete]` | 指定要对打印作业执行的操作。 如果指定了作业编号，但未指定任何操作，则会显示有关打印作业的信息。<ul><li>**/hold** -延迟作业，允许其他打印作业绕过它。</li><li>**/release** -释放已延迟的打印作业。</li><li>**/delete** -从打印队列中删除打印作业。</li></ul> |
| help | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 该 `net print\\<computername>` 命令显示有关共享打印机队列中的打印作业的信息。 下面的示例显示了名为*激光器*的共享打印机的队列中所有打印作业的报表：

    ```
    printers at \\PRODUCTION
    Name              Job #      Size      Status
    -----------------------------
    LASER Queue       3 jobs               *printer active*
    USER1          84        93844      printing
    USER2          85        12555      Waiting
    USER3          86        10222      Waiting
    ```

- 下面是打印作业报表的示例：

    ```
    Job #            35
    Status           Waiting
    Size             3096
    remark
    Submitting user  USER2
    Notify           USER2
    Job data type
    Job parameters
    additional info
    ```

### <a name="examples"></a>示例

若要列出* \\ 生产*计算机上*Dotmatrix*打印队列的内容，请键入：

```
net print \\Production\Dotmatrix
```

若要显示有关* \\ 生产*计算机上作业编号*35*的信息，请键入：

```
net print \\Production 35
```

若要在* \\ 生产*计算机上延迟作业编号*263* ，请键入：

```
net print \\Production 263 /hold
```

若要在* \\ 生产*计算机上发布作业编号*263* ，请键入：

```
net print \\Production 263 /release
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)

- [prnjobs 命令](prnjobs.md)

- [Windows 管理规范 (WMI)](https://docs.microsoft.com/windows/win32/wmisdk/wmi-start-page)

- [Powershell 中的 Printmanagement.msc](https://docs.microsoft.com/powershell/module/printmanagement)

- [面向 IT 专业人员的脚本资源](https://gallery.technet.microsoft.com/ScriptCenter/site/search?f%5B0%5D.Type=RootCategory&f%5B0%5D.Value=printing&f%5B0%5D.Text=Printing)
