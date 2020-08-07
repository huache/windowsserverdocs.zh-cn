---
title: create volume mirror
description: 创建卷镜像命令的参考文章，它使用两个指定的动态磁盘创建卷镜像。
ms.topic: article
ms.assetid: 48776917-783a-47ff-8da4-1cab77cea34b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f25c78a49393a0c48330a7b705c14b906f827c33
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87879854"
---
# <a name="create-volume-mirror"></a>create volume mirror

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用两个指定的动态磁盘创建卷镜像。 创建卷后，焦点会自动转移到新卷。

## <a name="syntax"></a>语法

```
create volume mirror [size=<n>] disk=<n>,<n>[,<n>,...] [align=<n>] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 大小 =`<n>` | 指定卷在每个磁盘上占用的磁盘空间量（以兆字节 (MB) 为单位）。 如果没有指定大小，新建卷将占据最小磁盘上的剩余可用空间以及其他磁盘上相同大小的空间。 |
| disk = `<n>` ， `<n>` [ `,<n>,...` ] | 指定在其上创建镜像卷的动态磁盘。 需要两个动态磁盘来创建镜像卷。 在每个磁盘上分配的空间量等于使用**size**参数指定的大小。 |
| align =`<n>` | 将所有卷区与最接近的对齐边界对齐。 此参数通常与硬件 RAID 逻辑单元号（ (LUN) 阵列一起使用，以提高性能。 `<n>`从磁盘开始到最接近的对齐边界 (KB) 的千字节数。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误。 |

## <a name="examples"></a>示例

若要创建大小为 1000 mb 的镜像卷，请在磁盘1和2上键入：

```
create volume mirror size=1000 disk=1,2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [create 命令](create.md)
