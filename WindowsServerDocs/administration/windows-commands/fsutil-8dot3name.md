---
title: fsutil 8dot3name
description: Fsutil 8dot3name 命令的参考主题，查询或更改短名称（8dot3 名称）行为的设置。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: a0c6dbfe-d898-496d-9356-825f7fbd90ec
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 02977a33c21560fd2078f0f596f312f4ab4bc408
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436052"
---
# <a name="fsutil-8dot3name"></a>fsutil 8dot3name

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

查询或更改短名称（8dot3 名称）行为的设置，其中包括：

- 查询短名称行为的当前设置。

- 如果从指定的目录路径中去除短名称，则扫描可能会受到影响的注册表项的指定目录路径。

- 更改控制短名称行为的设置。 此设置可应用于指定的卷或默认的卷设置。

- 删除目录中所有文件的短名称。

> [!IMPORTANT]
> 永久删除8dot3 文件名，而不修改指向8dot3 文件名的注册表项可能会导致意外的应用程序故障，包括无法卸载应用程序。 建议你先备份目录或卷，然后再尝试删除8dot3 文件名。

## <a name="syntax"></a>语法

```
fsutil 8dot3name [query] [<volumepath>]
fsutil 8dot3name [scan] [/s] [/l [<log file>] ] [/v] <directorypath>
fsutil 8dot3name [set] { <defaultvalue> | <volumepath> {1|0}}
fsutil 8dot3name [strip] [/t] [/s] [/f] [/l [<log file.] ] [/v] <directorypath>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| query`[<volumepath>]` | 在文件系统中查询8dot3 短名称创建行为的状态。<p>如果未指定*volumepath*作为参数，则会显示所有卷的默认8dot3name 创建行为设置。 |
| 检测`<directorypath>` | 如果文件名称中去除了8dot3 短名称，则扫描可能会受到影响的指定*directorypath*中的文件。 |
| 字符集`<defaultvalue> | <volumepath>}` | 在以下实例中更改8dot3 名称创建的文件系统行为：<ul><li>如果指定了*defaultvalue* ，则注册表项**HKLM\System\CurrentControlSet\Control\FileSystem\NtfsDisable8dot3NameCreationNtfsDisable8dot3NameCreationNtfsDisable8dot3NameCreation**设置为*defaultvalue*。<p>*DefaultValue*可以具有以下值：<ul><li>**0**：为系统上的所有卷启用8dot3 名称创建。</li><li>**1**：为系统上的所有卷禁用8dot3 名称创建。</li><li>**2**：按卷设置8dot3 名称创建。</li><li>**3**：对于除系统卷之外的所有卷禁用8dot3 名称创建。</li></ul><li>指定*volumepath*时，磁盘上指定的卷标志8dot3name 属性设置为为指定的卷（**0**）启用8dot3 名称创建，或设置为在指定的卷上禁用8dot3 名称创建（**1**）。<p>您必须将8dot3 名称创建的默认文件系统行为设置为值**2** ，然后才能启用或禁用指定卷的8dot3 名称创建。</li></ul> |
| 条形`<directorypath>` | 删除位于指定*directorypath*中的所有文件的8dot3 文件名。 如果任何文件的*directorypath*与文件名一起包含的字符超过260个字符，则不会删除该文件的8dot3 文件名。<p>此命令会列出，但不会修改指向永久删除了8dot3 文件名称的文件的注册表项。 |
| `<volumepath>` | 指定驱动器名称后跟冒号或 GUID （格式为） `volume{GUID}` 。 |
| /f | 指定位于指定*directorypath*中的所有文件都具有删除的8dot3 文件名，即使存在指向使用8dot3 文件名的文件的注册表项也是如此。 在这种情况下，操作将删除8dot3 文件名，但不会修改指向使用8dot3 文件名的文件的任何注册表项。 **警告：** 建议你在使用 **/f**参数之前备份目录或卷，因为这可能会导致意外的应用程序故障，包括无法卸载程序。 |
| /l`[<log file>]` | 指定写入信息的日志文件。<p>如果未指定 **/l**参数，则所有信息都会写入默认日志文件： `%temp%\8dot3_removal_log@(GMT YYYY-MM-DD HH-MM-SS)` .log * * |
| /s | 指定应将操作应用到指定*directorypath*的子目录。 |
| /t  | 指定是否应在测试模式下运行8dot3 文件名的删除操作。 执行除删除8dot3 文件名之外的所有操作。 你可以使用测试模式来了解哪些注册表项指向使用8dot3 文件名的文件。 |
| /v | 指定写入日志文件的所有信息也会显示在命令行上。 |

### <a name="examples"></a>示例

若要查询使用 GUID "{928842df-5a01-11de-a85c-806e6f6e6963}" 指定的磁盘卷的 "禁用8dot3 名称" 行为，请键入：

```
fsutil 8dot3name query volume{928842df-5a01-11de-a85c-806e6f6e6963}
```

还可以通过使用 "**行为**" 子命令查询8dot3 名称行为。

若要删除*D:\MyData*目录和所有子目录中的8dot3 文件名，并将该信息写入指定为*mylogfile.txt*的日志文件，请键入：

```
fsutil 8dot3name strip /l mylogfile.log /s d:\MyData
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)

- [fsutil behavior](fsutil-behavior.md)
