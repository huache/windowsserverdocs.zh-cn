---
title: fsutil resource
description: 用于管理事务资源管理器及其行为的 fsutil resource 命令的参考文章。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: b198d8ca-a5b7-430f-8911-5cbb9f50484c
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: c0be84f00df2e0010f6c2a318f605532a3bc4d23
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86958179"
---
# <a name="fsutil-resource"></a>fsutil resource

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

创建辅助事务资源管理器，启动或停止事务资源管理器，或显示有关事务资源管理器的信息，并修改以下行为：

- 默认事务资源管理器在下一次装入时是否清除其事务元数据。

- 指定的事务资源管理器，以优先于可用性。

- 指定的事务资源管理器优先于可用性。

- 正在运行的事务性资源管理器的特性。

## <a name="syntax"></a>语法

```
fsutil resource [create] <rmrootpathname>
fsutil resource [info] <rmrootpathname>
fsutil resource [setautoreset] {true|false} <Defaultrmrootpathname>
fsutil resource [setavailable] <rmrootpathname>
fsutil resource [setconsistent] <rmrootpathname>
fsutil resource [setlog] [growth {<containers> containers|<percent> percent} <rmrootpathname>] [maxextents <containers> <rmrootpathname>] [minextents <containers> <rmrootpathname>] [mode {full|undo} <rmrootpathname>] [rename <rmrootpathname>] [shrink <percent> <rmrootpathname>] [size <containers> <rmrootpathname>]
fsutil resource [start] <rmrootpathname> [<rmlogpathname> <tmlogpathname>
fsutil resource [stop] <rmrootpathname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| create | 创建辅助事务资源管理器。 |
| `<rmrootpathname>` | 指定事务资源管理器根目录的完整路径。 |
| info | 显示指定的事务性资源管理器的信息。 |
| setautoreset | 指定默认的事务资源管理器是否将在下一次装入时清除事务元数据。<ul><li>**true** -指定事务资源管理器在默认情况下将在下一次装入时清除事务元数据。</li><li>**false** -指定事务资源管理器默认情况下不会清除下一次装入时的事务性元数据。 |
| `<defaultrmrootpathname>` | 指定驱动器名称后跟一个冒号。 |
| setavailable | 指定事务资源管理器优先于可用性。 |
| setconsistent | 指定事务资源管理器将优先于可用性。 |
| setlog | 更改已在运行的事务性资源管理器的特性。 |
| growth | 指定事务资源管理器日志可增长的量。<p>可按如下所示指定增长参数：<ul><li>容器数，使用格式：`<containers> containers`</li><li>百分比，使用格式：`<percent> percent`</li></ul> |
| `<containers>` | 指定事务性资源管理器使用的数据对象。 |
| maxextent | 指定指定的事务资源管理器的最大容器数。 |
| minextent | 指定指定的事务资源管理器的最小容器数。 |
| 众`{full|undo}` | 指定是记录所有事务（ **full**）还是只记录回滚事件（**undo**）。 |
| 重命名 | 更改事务资源管理器的 GUID。 |
| 缩减 | 指定事务资源管理器日志可自动减少的百分比。 |
| 大小 | 指定事务资源管理器的大小，以指定数目的*容器*。 |
| start | 启动指定的事务资源管理器。 |
| stop | 停止指定的事务资源管理器。 |

### <a name="examples"></a>示例

若要设置*c:\test*指定的事务资源管理器的日志，以自动增长5个容器，请键入：

```
fsutil resource setlog growth 5 containers c:test
```

若要设置*c:\test*指定的事务资源管理器的日志，以自动增长两个百分比，请键入：

```
fsutil resource setlog growth 2 percent c:test
```

若要指定默认的事务资源管理器将在驱动器 C 上的下一个装载中清除事务元数据，请键入：

```
fsutil resource setautoreset true c:\
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)

- [事务性 NTFS](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc730726(v=ws.10))
