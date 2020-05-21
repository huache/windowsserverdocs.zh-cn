---
title: fsutil volume
description: 适用于 fsutil volume 命令的参考主题，用于卸载卷，或在硬盘驱动器上查询硬盘驱动器，以确定硬盘驱动器上当前可用的可用空间量，或使用特定群集的文件。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 0397c204-b3f8-4fd8-b71d-b7efb117766d
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 18671447664c47af48b4ca074aab823fd2b78625
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436832"
---
# <a name="fsutil-volume"></a>fsutil volume

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

卸载卷，或查询硬盘驱动器，确定硬盘驱动器上当前可用的可用空间量，或使用特定群集的文件。

## <a name="syntax"></a>语法

```
fsutil volume [allocationreport] <volumepath>
fsutil volume [diskfree] <volumepath>
fsutil volume [dismount] <volumepath>
fsutil volume [filelayout] <volumepath> <fileID>
fsutil volume [list]
fsutil volume [querycluster] <volumepath> <cluster> [<cluster>] … …
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| allocationreport | 显示有关在给定卷上如何使用存储的信息。 |
| `<volumepath>` | 指定驱动器号（后跟冒号）。 |
| diskfree | 查询硬盘驱动器以确定其上的可用空间量。 |
| 卸载 | 卸载卷。 |
| filelayout | 显示给定文件的 NTFS 元数据。 |
| `<fileID>` | 指定文件 id。 |
| list | 列出系统上的所有卷。 |
| querycluster | 查找使用指定群集的文件。 可以指定包含**querycluster**参数的多个群集。 |
| `<cluster>` | 指定逻辑群集号（LCN）。 |

### <a name="examples"></a>示例

若要显示分配的群集报告，请键入：

```
fsutil volume allocationreport C:
```

若要卸除驱动器 C 上的卷，请键入：

```
fsutil volume dismount c:
```

若要查询驱动器 C 上卷的可用空间量，请键入：

```
fsutil volume diskfree c:
```

若要显示有关指定文件的所有信息，请键入：

```
fsutil volume C: *
fsutil volume C:\Windows
fsutil volume C: 0x00040000000001bf
```

若要列出磁盘上的卷，请键入：

```
fsutil volume list
```

若要在驱动器 C 上查找使用由逻辑群集号50和0x2000 指定的群集的文件，请键入：

```
fsutil volume querycluster C: 50 0x2000
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)

- [NTFS 的工作方式](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781134(v=ws.10))
