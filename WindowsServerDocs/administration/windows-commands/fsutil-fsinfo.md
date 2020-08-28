---
title: Fsutil fsinfo
description: 适用于 fsutil fsinfo 命令的参考文章，其中列出了所有驱动器、查询驱动器类型、查询卷信息、查询特定于 NTFS 的卷信息或查询文件系统统计信息。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: 7787a72e-a26b-415f-b700-a32806803478
ms.topic: reference
ms.date: 10/16/2017
ms.openlocfilehash: e921b8572b7d1d87a1baf40cfdbc955adce3ec01
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037365"
---
# <a name="fsutil-fsinfo"></a>fsutil fsinfo

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

列出所有驱动器、查询驱动器类型、查询卷信息、查询特定于 NTFS 的卷信息或查询文件系统统计信息。

## <a name="syntax"></a>语法

```
fsutil fsinfo [drives]
fsutil fsinfo [drivetype] <volumepath>
fsutil fsinfo [ntfsinfo] <rootpath>
fsutil fsinfo [statistics] <volumepath>
fsutil fsinfo [volumeinfo] <rootpath>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| 驱动器 | 列出计算机中的所有驱动器。 |
| drivetype | 查询驱动器并列出其类型，如 cd-rom 驱动器。 |
| ntfsinfo | 列出指定卷的 NTFS 特定卷信息，如扇区数、群集总数、可用群集以及 MFT 区的开头和结尾。 |
| sectorinfo | 列出有关硬件的扇区大小和对齐方式的信息。 |
| statistics | 列出指定卷的文件系统统计信息，如元数据、日志文件和 MFT 读取和写入。 |
| volumeinfo | 列出指定卷的信息，例如文件系统、卷是否支持区分大小写的文件名、文件名中的 unicode 或磁盘配额，或是 DirectAccess (DAX) 卷。 |
| `<volumepath>:` | 指定驱动器号 (后跟冒号) 。 |
| `<rootpath>:` | 指定驱动器号 (后跟根驱动器的冒号) 。 |

### <a name="examples"></a>示例

若要列出计算机中的所有驱动器，请键入：

```
fsutil fsinfo drives
```

类似于以下内容的输出：

```
Drives: A:\ C:\ D:\ E:\
```

若要查询驱动器 C 的驱动器类型，请键入：

```
fsutil fsinfo drivetype c:
```

查询的可能结果包括：

```
Unknown Drive
No such Root Directory
Removable Drive, for example floppy
Fixed Drive
Remote/Network Drive
CD-ROM Drive
Ram Disk
```

若要查询 volume E 的卷信息，请键入：

```
fsinfo volumeinfo e:\
```

类似于以下内容的输出：

```
Volume Name : Volume
Serial Number : 0xd0b634d9
Max Component Length : 255
File System Name : NTFS
Supports Named Streams
Is DAX Volume
```

若要在驱动器 F 中查询特定于 NTFS 的卷信息，请键入：

```
fsutil fsinfo ntfsinfo f:
```

类似于以下内容的输出：

```
NTFS Volume Serial Number : 0xe660d46a60d442cb
Number Sectors : 0x00000000010ea04f
Total Clusters : 0x000000000021d409
Mft Zone End : 0x0000000000004700
```

若要查询文件系统的基本硬件以获取扇区信息，请键入：

```
fsinfo sectorinfo d:
```

类似于以下内容的输出：

```
D:\>fsutil fsinfo sectorinfo d:
LogicalBytesPerSector : 4096
PhysicalBytesPerSectorForAtomicity : 4096
Trim Not Supported
DAX capable
```

若要查询驱动器 E 的文件系统统计信息，请键入：

```
fsinfo statistics e:
```

类似于以下内容的输出：

```
File System Type : NTFS
Version : 1
UserFileReads : 75021
UserFileReadBytes : 1305244512
LogFileWriteBytes : 180936704
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
