---
title: fsutil repair
description: Fsutil repair 命令的参考主题，用于管理和监视 NTFS 自修复修复操作。
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
ms.assetid: 62d77150-1d9e-4069-ab4a-299f33024912
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 449bd39b6b2df0e302085b71ef9db87d2020b0f0
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83435752"
---
# <a name="fsutil-repair"></a>fsutil repair

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

管理和监视 NTFS 自修复修复操作。 自愈 NTFS 会尝试联机更正 NTFS 文件系统的损坏，而无需运行**chkdsk.exe** 。 有关详细信息，请参阅[自愈 NTFS](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771388(v=ws.10))。

## <a name="syntax"></a>语法

```
fsutil repair [enumerate] <volumepath> [<logname>]
fsutil repair [initiate] <volumepath> <filereference>
fsutil repair [query] <volumepath>
fsutil repair [set] <volumepath> <flags>
fsutil repair [wait][<waittype>] <volumepath>

```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 列举 | 枚举卷损坏日志的条目。 |
| `<logname>` | 可以是 `$corrupt` 卷中已确认的损坏的集合，或 `$verify` 卷中一组潜在的未验证损坏。 |
| 造成 | 启动 NTFS 自修复。 |
| `<filereference>` | 指定 NTFS 特定于卷的文件 ID （文件参考编号）。 文件引用包含文件的段号。 |
| 查询 | 查询 NTFS 卷的自愈状态。 |
| set | 设置卷的自愈状态。 |
| `<flags>` | 指定设置卷的自愈状态时要使用的修复方法。<p>此参数可设置为三个值：<ul><li>**0x01** -启用常规修复。</li><li>**0x09** -无需修复就可能丢失数据。</li><li>**0x00** -禁用 NTFS 自修复修复操作。</li></ul> |
| state | 查询系统或给定卷的损坏状态。 |
| wait | 等待修复完成。 如果 NTFS 检测到它在其上执行修复的卷上存在问题，则此选项允许系统等待修复完成，然后再运行挂起的任何脚本。 |
| `[waittype {0|1}]` | 指示是等待当前修复完成，还是等待所有修复完成。 *Waittype*参数可设置为以下值：<ul><li>**0** -等待所有修复完成。 （默认值）</li><li>**1** -等待当前修复完成。</li></ul> |

### <a name="examples"></a>示例

若要枚举已确认损坏的卷，请键入：

```
fsutil repair enumerate C: $Corrupt
```

若要启用驱动器 C 上的自愈修复，请键入：

```
fsutil repair set c: 1
```

若要禁用驱动器 C 上的自修复修复，请键入：

```
fsutil repair set c: 0
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)

- [自修复 NTFS](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771388(v=ws.10))
