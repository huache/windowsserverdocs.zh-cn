---
title: fsutil usn
description: 适用于 fsutil usn 命令的参考文章，该命令管理 (USN) change 日记本的更新序列号。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: faad34aa-4ba1-4129-bc1f-08088399e2fa
ms.topic: reference
ms.date: 10/16/2017
ms.openlocfilehash: 551324f3a356d7ca3ebce617853000baee3c68e0
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032925"
---
# <a name="fsutil-usn"></a>fsutil usn

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

管理 (USN) change 日记本的更新序列号。 USN 更改日志提供对卷上的文件所做的所有更改的持久日志。 添加、删除和修改文件、目录和其他 NTFS 对象时，NTFS 会将记录输入 USN 更改日志，每个文件对应于计算机上的一个卷。 每条记录都指明了变更的类型以及所更改的对象。 新记录将追加到流的末尾。

## <a name="syntax"></a>语法

```
fsutil usn [createjournal] m=<maxsize> a=<allocationdelta> <volumepath>
fsutil usn [deletejournal] {/d | /n} <volumepath>
fsutil usn [enablerangetracking] <volumepath> [options]
fsutil usn [enumdata] <fileref> <lowUSN> <highUSN> <volumepath>
fsutil usn [queryjournal] <volumepath>
fsutil usn [readdata] <filename>
fsutil usn [readjournal] [c= <chunk-size> s=<file-size-threshold>] <volumepath>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| createjournal | 创建 USN 更改日志。 |
| m =`<maxsize>` | 指定 NTFS 为变更日志分配的最大大小（以字节为单位）。 |
| a =`<allocationdelta>` | 指定添加到末尾并从变更日志的开头删除的内存分配的大小（以字节为单位）。 |
| `<volumepath>` | 指定驱动器号 (后跟冒号) 。 |
| deletejournal | 删除或禁用活动的 USN 更改日志。<p>**警告：** 删除变更日志会影响文件复制服务 (FRS) 和索引服务，因为这需要这些服务执行卷的完整 (和耗时的) 扫描。 这反过来会影响 FRS SYSVOL 复制，并在重新扫描卷时 DFS 链接备用项之间进行复制。 |
| /d | 禁用活动的 USN 更改日志，并在禁用更改日志时返回输入/输出 (i/o) 控制。 |
| /n | 禁用活动的 USN 更改日志，并在禁用更改日志后返回 i/o 控制。 |
| enablerangetracking | 为卷启用 USN 写入范围跟踪。 |
| c =`<chunk-size>` | 指定要在卷上跟踪的区块大小。 |
| s =`<file-size-threshold>` | 指定范围跟踪的文件大小阈值。 |
| enumdata | 枚举并列出两个指定边界之间的变更日志项。 |
| `<fileref>` | 指定要开始枚举的卷上的文件中的序号位置。 |
| `<lowUSN>` | 指定用于筛选返回的记录的 USN 值范围的下限。 仅返回最新的更改日志 USN 介于 *lowUSN* 和 *highUSN* 成员值之间的记录。 |
| `<highUSN>` | 指定用于筛选返回的文件的 USN 值范围上限。 |
| queryjournal | 查询卷的 USN 数据以收集有关当前更改日志、记录和其容量的信息。 |
| readdata | 读取文件的 USN 数据。 |
| `<filename>` | 指定文件的完整路径，包括文件名和扩展名（例如）： *C:\documents\filename.txt*。 |
| readjournal | 读取 USN 日志中的 USN 记录。 |
| minver =`<number>` | 要返回的 USN_RECORD 的最低主要版本。 默认值为2。 |
| maxver =`<number>` | 要返回的 USN_RECORD 的最大主版本。 默认值 = 4。 |
| startusn =`<USN number>` | 要开始从读取 USN 日志的 USN。 默认值 = 0。 |

#### <a name="remarks"></a>注解

- 程序可以参考 USN 更改日志来确定对一组文件进行的所有修改。 与检查时间戳或注册文件通知相比，USN 更改日志的效率要高得多。 USN 更改日志由索引服务启用和使用，文件复制服务 (FRS) 、远程安装服务 (RIS) 和远程存储。

- 如果卷上已存在更改日志，则 **createjournal** 参数将更新变更日志的 **maxsize** 和 **allocationdelta** 参数。 这使您可以展开活动日志维护的记录数量，而不必禁用该日志。

- 更改日志会增长到大于此目标值，但更改日志将在下一个 NTFS 检查点被截断为小于此值。 NTFS 检查变更日志，并在其大小超过 **maxsize** 的值和 **allocationdelta**值时对其进行修整。 在 NTFS 检查点，操作系统将记录写入 NTFS 日志文件，该文件可使 NTFS 确定从故障中恢复所需的处理。

- 在修整之前，变更日志可能会增长到大于 **maxsize** 和 **allocationdelta** 值的总和。

- 删除或禁用活动更改日志非常耗时，因为系统必须访问主文件表 (MFT) 中的所有记录，并将最后一个 USN 属性设置为 0 (零) 。 此过程可能需要几分钟的时间，如果需要重新启动，它可以在系统重新启动后继续。 在此过程中，变更日志不被视为处于活动状态，也不会被禁用。 当系统禁用日志时，无法访问它，所有日志操作都将返回错误。 禁用活动的日志时应特别小心，因为它会对其他使用该日志的应用程序产生负面影响。

### <a name="examples"></a>示例

若要在驱动器 C 上创建 USN 更改日志，请键入：

```
fsutil usn createjournal m=1000 a=100 c:
```

若要删除驱动器 C 上的活动 USN 更改日志，请键入：

```
fsutil usn deletejournal /d c:
```

若要使用指定的区块大小和文件大小阈值启用范围跟踪，请键入：

```
fsutil usn enablerangetracking c=16384 s=67108864 C:
```

若要枚举并列出驱动器 C 上两个指定边界之间的变更日志条目，请键入：

```
fsutil usn enumdata 1 0 1 c:
```

若要查询驱动器 C 上的卷的 USN 数据，请键入：

```
fsutil usn queryjournal c:
```

若要读取驱动器 C 上的 \Temp 文件夹中的文件的 USN 数据，请键入：

```
fsutil usn readdata c:\temp\sample.txt
```

若要读取具有特定开始 USN 的 USN 日志，请键入：

```
fsutil usn readjournal startusn=0xF00
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)
