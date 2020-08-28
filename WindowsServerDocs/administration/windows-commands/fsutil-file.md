---
title: fsutil file
description: Fsutil file 命令的参考文章，该命令按用户名查找文件，查询为文件分配的范围，设置文件的短名称，设置文件的有效数据长度，为文件设置零数据，或创建新的文件。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: 9f3dc104-dd69-4b03-b824-a29896780164
ms.topic: reference
ms.date: 10/16/2017
ms.openlocfilehash: 69ef36a03c22d7e14d4d657ce5ebab85b63afbd7
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037375"
---
# <a name="fsutil-file"></a>fsutil file

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

按用户名查找文件 (如果启用了磁盘配额) ，查询为文件分配的范围，设置文件的短名称，设置文件的有效数据长度，为文件设置零数据，或创建新的文件。

## <a name="syntax"></a>语法

```
fsutil file [createnew] <filename> <length>
fsutil file [findbysid] <username> <directory>
fsutil file [optimizemetadata] [/A] <filename>
fsutil file [queryallocranges] offset=<offset> length=<length> <filename>
fsutil file [queryextents] [/R] <filename> [<startingvcn> [<numvcns>]]
fsutil file [queryfileid] <filename>
fsutil file [queryfilenamebyid] <volume> <fileid>
fsutil file [queryoptimizemetadata] <filename>
fsutil file [queryvaliddata] [/R] [/D] <filename>
fsutil file [seteof] <filename> <length>
fsutil file [setshortname] <filename> <shortname>
fsutil file [setvaliddata] <filename> <datalength>
fsutil file [setzerodata] offset=<offset> length=<length> <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| createnew | 使用由零组成的内容创建具有指定名称和大小的文件。 |
| `<length>` | 指定文件的有效数据长度。 |
| findbysid | 在启用磁盘配额的 NTFS 卷上查找属于指定用户的文件。 |
| `<username>` | 指定用户的用户名或登录名。 |
| `<directory>` | 指定目录的完整路径，例如 C:\users。 |
| optimizemetadata | 这会对给定文件执行元数据的立即压缩。 |
| /a | 优化前和优化后分析文件元数据。 |
| queryallocranges | 查询 NTFS 卷上的文件的分配范围。 用于确定文件是否具有稀疏区域。 |
| offset =`<offset>` | 指定范围的开始时间，该范围应设置为零。 |
| 长度 =`<length>` | 指定范围 (的长度，以字节为单位) 。 |
| queryextents | 查询文件的范围。 |
| /r | 如果 <filename> 是重新分析点，请将其打开而不是其目标。 |
| `<startingvcn>` | 指定要查询的第一个 VCN。 如果省略，则从 VCN 0 开始。 |
| `<numvcns>` | 要查询的 VCNs 的数目。 如果省略或为0，则查询到 EOF。 |
| queryfileid | 查询 NTFS 卷上文件的文件 ID。 |
| `<volume>` | 指定卷作为驱动器名称后跟一个冒号。 |
| queryfilenamebyid | 显示 NTFS 卷上指定文件 ID 的随机链接名称。 由于一个文件可以有多个指向该文件的链接名称，因此不能保证将提供哪个文件链接作为文件名的查询结果。 |
| `<fileid>` | 指定 NTFS 卷上的文件的 ID。 |
| queryoptimizemetadata | 查询文件的元数据状态。 |
| queryvaliddata | 查询文件的有效数据长度。 |
| /d | 显示详细的有效数据信息。 |
| seteof | 设置给定文件的 EOF。 |
| setshortname | 为 NTFS 卷上的文件设置短名称 (8.3 字符长度文件名) 。 |
| `<shortname>` | 指定文件的短名称。 |
| setvaliddata | 为 NTFS 卷上的文件设置有效的数据长度。 |
| `<datalength>` | 指定文件的长度（以字节为单位）。 |
| setzerodata | 将 (的 *偏移量* 和 *长度*) 指定的范围设置为零，这将清空文件。 如果该文件是稀疏文件，则退回基础分配单元。 |

#### <a name="remarks"></a>注解

- 在 NTFS 中，文件长度有两个重要概念：文件尾 (EOF) 标记和有效数据长度 (VDL) 。 EOF 指示文件的实际长度。 VDL 标识磁盘上有效数据的长度。 VDL 和 EOF 之间的任何读取都将自动返回0以保留 C2 对象重用要求。

- **Setvaliddata**参数仅适用于管理员，因为它需要执行卷维护任务 (SeManageVolumePrivilege) 特权。 此功能仅适用于高级多媒体和系统区域网络方案。 **Setvaliddata**参数必须是大于当前 VDL 的正数值，但小于当前文件大小。

    在以下情况，程序可以设置 VDL：

    - 通过硬件通道将原始群集直接写入磁盘。 这允许程序通知文件系统此范围包含可以返回给用户的有效数据。

    - 在性能问题时创建大型文件。 这可以避免在文件创建或扩展时用零填充文件所花费的时间。

### <a name="examples"></a>示例

若要在驱动器 C 上查找 *scottb* 拥有的文件，请键入：

```
fsutil file findbysid scottb c:\users
```

若要在 NTFS 卷上查询文件的分配范围，请键入：

```
fsutil file queryallocranges offset=1024 length=64 c:\temp\sample.txt
```

若要优化文件的元数据，请键入：

```
fsutil file optimizemetadata C:\largefragmentedfile.txt
```

若要查询文件的范围，请键入：

```
fsutil file queryextents C:\Temp\sample.txt
```

若要设置文件的 EOF，请键入：

```
fsutil file seteof C:\testfile.txt 1000
```

若要设置文件的短名称，请 *longfilename.txt* 在驱动器 C 上 *longfile.txt*，键入：

```
fsutil file setshortname c:\longfilename.txt longfile.txt
```

若要将名为*testfile.txt*的文件的有效数据长度设置为*4096 字节*，请键入：

```
fsutil file setvaliddata c:\testfile.txt 4096
```

若要将 NTFS 卷上的文件范围设置为零，以将其设置为零，请键入：

```
fsutil file setzerodata offset=100 length=150 c:\temp\sample.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
