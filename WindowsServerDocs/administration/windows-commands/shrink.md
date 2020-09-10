---
title: 缩减
description: 用于 DiskPart shrink 的参考文章，可按指定的量减小所选卷的大小。
ms.topic: reference
ms.assetid: ec87cc7c-9846-465e-a10d-4ee10db4f4e6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2fdfc8ba34f4e91bfafa1f8bf5341f9e4186cb5d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640943"
---
# <a name="shrink"></a>缩减

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

Diskpart shrink 命令按指定的数量减小所选卷的大小。 此命令可在卷末尾的未使用空间提供可用磁盘空间。

## <a name="syntax"></a>语法
```
shrink [desired=<n>] [minimum=<n>] [nowait] [noerr]
shrink querymax [noerr]
```
### <a name="parameters"></a>参数

|  参数  |                                                                                             说明                                                                                              |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| desired =<n> |                                                     指定希望该卷大小减少的空间量 (MB)。                                                     |
| 最小值 =<n> |                                                           指定该卷大小减少的最小空间量 (MB)。                                                           |
|  querymax   |                       返回可减少卷的最大空间量（以 MB 为单位）。 如果应用程序当前正在访问卷，则此值可能会发生变化。                        |
|   nowait    |                                                       强制该命令在收缩进程仍在进行的同时立即返回。                                                        |
|    noerr    | 仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="remarks"></a>备注
- 只有在使用 NTFS 文件系统格式化该卷或该卷上没有文件系统时，才能减少卷的大小。
- 此命令在基本卷以及简单或跨区动态卷上有效。
- 如果未指定所需的量，则该卷将按) 指定的最小数量减小 (。
- 如果未指定最小数量，则该卷将按所需量降低 (如果指定) 。
- 如果未指定最小数量和所需数量，则将尽可能减少该卷。
- 如果指定了最小数量但可用空间不足，则该命令将失败。
- 必须选择卷，此操作才能成功。 使用 " **选择音量** " 命令选择卷并将焦点移动到该卷。
- 此命令不会对原始设备制造商 (OEM) 分区、可扩展固件接口 (EFI) 系统分区或恢复分区。
  ## <a name="examples"></a>示例
  若要将所选卷的大小减小到250到 500 mb 之间的最大可能值，请键入：
  ```
  shrink desired=500 minimum=250
  ```
  若要显示可减少的卷的最大 MB 数，请键入：
  ```
  shrink querymax
  ```

[Resize-Partition](/powershell/module/storage/resize-partition?view=win10-ps)
