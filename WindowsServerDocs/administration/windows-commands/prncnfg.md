---
title: prncnfg
description: Prncnfg 命令的参考文章，它配置或显示有关打印机的配置信息。
ms.topic: reference
ms.assetid: 38a4e8fa-3122-495b-a125-35b926bc6415
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 2b72f453b016428537800997fc0a7056c211a3b2
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638364"
---
# <a name="prncnfg"></a>prncnfg

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

配置或显示有关打印机的配置信息。 此命令是位于目录中的 Visual Basic 脚本 `%WINdir%\System32\printing_Admin_Scripts\<language>` 。 若要在命令提示符下使用此命令，请键入 **cscript** ，然后键入 prncnfg 文件的完整路径，或将目录更改为相应的文件夹。 例如：`cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prncnfg`。

## <a name="syntax"></a>语法

```
cscript prncnfg {-g | -t | -x | -?} [-S <Servername>] [-P <Printername>] [-z <newprintername>] [-u <Username>] [-w <password>] [-r <portname>] [-l <location>] [-h <sharename>] [-m <comment>] [-f <separatorfilename>] [-y <datatype>] [-st <starttime>] [-ut <untiltime>] [-i <defaultpriority>] [-o <priority>] [<+|->shared] [<+|->direct] [<+|->hidden] [<+|->published] [<+|->rawonly] [<+|->queued] [<+|->enablebidi] [<+|->keepprintedjobs] [<+|->workoffline] [<+|->enabledevq] [<+|->docompletefirst]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| -g | 显示有关打印机的配置信息。 |
| -t | 配置打印机。 |
| -X | 重命名打印机。 |
| -S `<Servername>` | 指定承载要管理的打印机的远程计算机的名称。 如果未指定计算机，则使用本地计算机。 |
| -P `<Printername>` | 指定要管理的打印机的名称。 必需。 |
| -z `<newprintername>` | 指定新的打印机名称。 需要 **-x** 和 **-P** 参数。 |
| -u `<Username>` -w `<password>` | 指定有权连接到承载要管理的打印机的计算机的帐户。 目标计算机的本地管理员组的所有成员都具有这些权限，但也可以向其他用户授予权限。 如果未指定帐户，则必须使用具有这些权限的帐户登录，才能使命令正常工作。 |
| -r `<portname>` | 指定打印机的连接端口。 如果这是并行端口或串行端口，请使用端口 ID (例如，LPT1 或 COM1) 。 如果这是 TCP/IP 端口，请使用添加端口时指定的端口名称。 |
| -l `<location>` | 指定打印机位置，如 **Copyroom**。 如果位置中包含空格，请使用引号将文本括起来，如 **"复制房间"**。|
| -h `<sharename>` | 指定打印机的共享名。 |
| -m `<comment>` | 指定打印机的注释字符串。 |
| -f `<separatorfilename>` | 指定一个文件，该文件包含在 "分隔符" 页上显示的文本。 |
| -y `<datatype>` | 指定打印机可接受的数据类型。 |
| -st `<starttime>` | 配置打印机的可用性有限。 指定打印机的可用时间。 如果将文档发送到打印机时无法使用，则会将文档保存 (后台处理) ，直到打印机可用为止。 必须将时间指定为24小时制。 例如，若要指定 11:00 P.M.，请键入 **2300**。 |
| -未 `<endtime>` | 配置打印机的可用性有限。 指定打印机不再可用的时间。 如果将文档发送到打印机时无法使用，则会将文档保存 (后台处理) ，直到打印机可用为止。 必须将时间指定为24小时制。 例如，若要指定 11:00 P.M.，请键入 **2300**。 |
| -o `<priority>` | 指定后台处理程序用于将打印作业路由到打印队列的优先级。 优先级较高的打印队列会在具有较低优先级的任何队列之前接收其所有作业。 |
| -i `<defaultpriority>` | 指定分配给每个打印作业的默认优先级。 |
| `{+|-}`共享 | 指定是否在网络上共享此打印机。 |
| `{+|-}`直 | 指定是否应将文档直接发送到打印机而不进行后台处理。 |
| `{+|-}`发布 | 指定是否应在 active directory 中发布此打印机。 如果您发布打印机，其他用户可以根据其位置和功能 (例如彩色打印和装订) 搜索该打印机。 |
| `{+|-}`隐藏 | Reserved 函数。 |
| `{+|-}`rawonly | 指定是否只有原始数据打印作业可以在此队列中进行后台处理。 |
| `{+|-}`} 已排队 | 指定在文档的最后一页进行后台处理之前，打印机不应该开始打印。 打印程序在文档完成打印之前不可用。 但是，使用此参数可确保整个文档可用于打印机。 |
| `{+|-}`keepprintedjobs | 指定后台处理程序在打印后是否应保留文档。 启用此选项后，用户可以从打印队列（而不是打印程序）将文档提交到打印机。 |
| `{+|-}`workoffline | 指定如果计算机未连接到网络，用户是否能够将打印作业发送到打印队列。 |
| `{+|-}`enabledevq | 指定打印作业是否不符合打印机设置 (例如，假脱机到非 PostScript 打印机的 PostScript 文件) 应保留在队列中，而不是打印。 |
| `{+|-}`docompletefirst | 指定后台处理程序是否应发送具有较低优先级的打印作业，该作业在发送具有较高优先级且未完成后台处理的打印作业之前已经完成后台处理。 如果启用此选项，并且没有文档完成后台处理，则后台处理程序将在较小的文档之前发送更大的文档。 如果要以作业优先级的成本最大程度地提高打印机效率，则应启用此选项。 如果禁用此选项，则后台处理程序始终首先向其各自的队列发送更高优先级的作业。 |
| `{+|-}`enablebidi | 指定打印机是否将状态信息发送到后台处理程序。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要使用名为*HRServer*的远程计算机承载的打印队列显示名为*colorprinter_2*打印机的配置信息，请键入：

```
cscript prncnfg -g -S HRServer -P colorprinter_2
```

若要配置名为 *colorprinter_2* 的打印机，以便在打印作业后，名为 *HRServer* 的远程计算机上的后台处理程序保留打印作业，请键入：

```
cscript prncnfg -t -S HRServer -P colorprinter_2 +keepprintedjobs
```

若要将名为 *HRServer* 的远程计算机上的打印机名称从 *colorprinter_2* 更改为 *colorprinter 3*，请键入：

```
cscript prncnfg -x -S HRServer -P colorprinter_2 -z "colorprinter 3"
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)
