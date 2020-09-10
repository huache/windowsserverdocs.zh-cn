---
title: msinfo32
description: 有关 msinfo32 命令的参考文章，它打开 "系统信息" 工具以显示本地计算机上的硬件、系统组件和软件环境的综合视图。
ms.topic: reference
ms.assetid: a38f31d7-1766-4103-becc-9d0b87c2826d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c3f82d95a3a2d62c03ebe78a6ac067e0574bc8c3
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640554"
---
# <a name="msinfo32"></a>msinfo32

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

打开 "系统信息" 工具，以显示本地计算机上的硬件、系统组件和软件环境的综合视图。

某些系统信息类别包含大量数据。 可以使用 **start/wait** 命令优化这些类别的报告性能。 有关详细信息，请参阅 [系统信息](/previous-versions/windows/it-pro/windows-server-2003/cc783305(v=ws.10))。

## <a name="syntax"></a>语法

```
msinfo32 [/pch] [/nfo <path>] [/report <path>] [/computer <computername>] [/showcategories] [/category <categoryID>] [/categories {+<categoryID>(+<categoryID>)|+all(-<categoryID>)}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<path>` | 指定要以 *C:\Folder1\File1.xxx*格式打开的文件，其中 *C* 是驱动器号， *Folder1* 是文件夹， *File1* 是文件名， *xxx* 是文件扩展名。<p>此文件可以是 **.nfo**、 **.xml**、 **.txt**或 **.cab** 文件。 |
| `<computername>` | 指定目标或本地计算机的名称。 这可以是 UNC 名称、IP 地址或完整的计算机名称。 |
| `<categoryID>` | 指定类别项的 ID。 可以使用 **/showcategories**获取类别 ID。 |
| /pch | 在 "系统信息" 工具中显示系统历史记录视图。 |
| /nfo | 将导出的文件保存为 **.nfo** 文件。 如果 *路径* 中指定的文件名不以 **.nfo** 扩展名结尾，则会自动将 **.nfo** 扩展名追加到文件名。 |
| /report | 将该文件以文本文件的形式保存在 *路径* 中。 文件名与在 *路径*中显示的内容完全相同。 不会将 .txt 扩展名追加到该文件中，除非在 path 中指定了它。 |
| /computer | 启动指定远程计算机的系统信息工具。 您必须具有相应的权限才能访问远程计算机。 |
| /showcategories | 启动系统信息工具，其中显示了所有可用的类别 Id，而不是显示友好名称或本地化名称。 例如，"软件环境" 类别显示为 " **SWEnv** " 类别。 |
| /category | 启动所选指定类别的系统信息。 使用 **/showcategories** 可显示可用类别 id 的列表。 |
| /categories | 启动只显示指定类别或类别的系统信息。 它还将输出限制为所选类别。 使用 **/showcategories** 可显示可用类别 id 的列表。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要列出可用的类别 Id，请键入：

```
msinfo32 /showcategories
```

若要使用显示的所有可用信息（加载的模块除外）启动系统信息工具，请键入：

```
msinfo32 /categories +all -loadedmodules
```

若要显示 **系统摘要** 信息并创建名为 *syssum*的 .nfo 文件（其中包含 " **系统摘要** " 类别中的信息），请键入：

```
msinfo32 /nfo syssum.nfo /categories +systemsummary
```

若要显示资源冲突信息，并创建一个名为 " *冲突*" 的 .nfo 文件，其中包含有关资源冲突的信息，请键入：

```
msinfo32 /nfo conflicts.nfo /categories +componentsproblemdevices+resourcesconflicts+resourcesforcedhardware
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
