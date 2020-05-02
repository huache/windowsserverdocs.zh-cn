---
title: prncnfg
description: 了解如何使用 prncfg 命令配置打印机。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 38a4e8fa-3122-495b-a125-35b926bc6415
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 49d079c8c659fc1f8abc821935c401ae00bc8ba4
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722853"
---
# <a name="prncnfg"></a>prncnfg

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

配置或显示有关打印机的配置信息。

## <a name="syntax"></a>语法
```
cscript Prncnfg {-g | -t | -x | -?} [-S <ServerName>] [-P <printerName>] [-z <NewprinterName>] [-u <UserName>] [-w <Password>] [-r <PortName>] [-l <Location>] [-h <Sharename>] [-m <Comment>] [-f <SeparatorFileName>] [-y <Datatype>] [-st <starttime>] [-ut <Untiltime>] [-i <DefaultPriority>] [-o <Priority>] [<+|->shared] [<+|->direct] [<+|->hidden] [<+|->published] [<+|->rawonly] [<+|->queued] [<+|->enablebidi] [<+|->keepprintedjobs] [<+|->workoffline] [<+|->enabledevq] [<+|->docompletefirst]
```

### <a name="parameters"></a>参数
|参数|描述|
|-------|--------|
|-g|显示有关打印机的配置信息。|
|-t|配置打印机。|
|-X|重命名打印机。|
|-S \<ServerName\>|指定承载要管理的打印机的远程计算机的名称。 如果未指定计算机，则使用本地计算机。|
|-P \<printerName\>|指定要管理的打印机的名称。 必需。|
|-z \<NewprinterName\>|指定新的打印机名称。 需要 **-x**和 **-P**参数。|
|-u \<用户名\> -w \<密码\>|指定有权连接到承载要管理的打印机的计算机的帐户。 目标计算机的本地管理员组的所有成员都具有这些权限，但也可以向其他用户授予权限。 如果未指定帐户，则必须使用具有这些权限的帐户登录，才能使命令正常工作。|
|-r \<portvalue\>|指定打印机的连接端口。 如果这是并行端口或串行端口，则使用端口的 ID （例如，LPT1 或 COM1）。 如果这是 TCP/IP 端口，请使用添加端口时指定的端口名称。|
|-l \<位置\>|指定打印机位置，如 "复制房间"。|
|-h \<共享名\>|指定打印机的共享名。|
|-m \<注释\>|指定打印机的注释字符串。|
|-f \<SeparatorFileName\>|指定一个文件，该文件包含在 "分隔符" 页上显示的文本。|
|-y \<数据类型\>|指定打印机可接受的数据类型。|
|-st \<starttime\>|配置打印机的可用性有限。 指定打印机的可用时间。 如果将文档发送到打印机时无法使用，则在打印机可用之前保存该文档（假脱机）。 必须将时间指定为24小时制。 例如，若要指定 11:00 P.M.，请键入**2300**。|
|-有\<Endtime Endtime\>|配置打印机的可用性有限。 指定打印机不再可用的时间。 如果将文档发送到打印机时无法使用，则在打印机可用之前保存该文档（假脱机）。 必须将时间指定为24小时制。 例如，若要指定 11:00 P.M.，请键入**2300**。|
|-o \<优先级\>|指定后台处理程序用于将打印作业路由到打印队列的优先级。 优先级较高的打印队列会在具有较低优先级的任何队列之前接收其所有作业。|
|-i \<DefaultPriority\>|指定分配给每个打印作业的默认优先级。|
|{+&#124;-} 共享|指定是否在网络上共享此打印机。|
|{+&#124;-} direct|指定是否应将文档直接发送到打印机而不进行后台处理。|
|{+&#124;-} 已发布|指定是否应在 active directory 中发布此打印机。 如果发布打印机，其他用户可以根据其位置和功能（如彩色打印和装订）搜索该打印机。|
|{+&#124;} 隐藏|Reserved 函数。|
|{+&#124;-} rawonly|指定是否只有原始数据打印作业可以在此队列中进行后台处理。|
|{+ &#124;-} 已排队|指定在文档的最后一页进行后台处理之前，打印机不应该开始打印。 打印程序在文档完成打印之前不可用。 但是，使用此参数可确保整个文档可用于打印机。|
|{+ &#124;-} keepprintedjobs|指定后台处理程序在打印后是否应保留文档。 启用此选项后，用户可以从打印队列（而不是打印程序）将文档提交到打印机。|
|{+ &#124;-} workoffline|指定如果计算机未连接到网络，用户是否能够将打印作业发送到打印队列。|
|{+ &#124;-} enabledevq|指定是否应将与打印机安装不匹配的打印作业（例如，假脱机的 PostScript 文件）保留在队列中，而不是打印。|
|{+ &#124;-} docompletefirst|指定后台处理程序是否应发送具有较低优先级的打印作业，该作业在发送具有较高优先级且未完成后台处理的打印作业之前已经完成后台处理。 如果启用此选项，并且没有文档完成后台处理，则后台处理程序将在较小的文档之前发送更大的文档。 如果要以作业优先级的成本最大程度地提高打印机效率，则应启用此选项。 如果禁用此选项，则后台处理程序始终首先向其各自的队列发送更高优先级的作业。|
|{+ &#124;-} enablebidi|指定打印机是否将状态信息发送到后台处理程序。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
-   **Prncnfg**命令是位于%windir%\system32\ printing_Admin_Scripts\\ <language>目录中的 Visual Basic 脚本。 若要使用此命令，请在命令提示符下键入**cscript** ，后跟 prncnfg 文件的完整路径，或将目录更改为相应的文件夹。 例如：
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prncnfg
    ```
-   如果提供的信息包含空格，请使用引号将文本括起来（例如， `"computer Name"`）。

## <a name="examples"></a><a name="BKMK_examples"></a>示例
若要使用名为 HRServer 的远程计算机承载的打印队列显示名为 colorprinter_2 打印机的配置信息，请键入：
```
cscript prncnfg -g -S HRServer -P colorprinter_2 
```

若要配置名为 colorprinter_2 的打印机，以便在打印作业后，名为 HRServer 的远程计算机上的后台处理程序保留打印作业，请键入：
```
cscript prncnfg -t -S HRServer -P colorprinter_2 +keepprintedjobs 
```

若要将名为 HRServer 的远程计算机上的打印机名称从 colorprinter_2 更改为 colorprinter 3，请键入：
```
cscript prncnfg -x -S HRServer -P colorprinter_2 -z "colorprinter 3" 
```

## <a name="additional-references"></a>其他参考
- [命令行语法密钥](command-line-syntax-key.md)
[打印命令参考](print-command-reference.md)
