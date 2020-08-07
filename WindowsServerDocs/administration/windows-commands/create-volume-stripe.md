---
title: create volume stripe
description: 创建卷条带化命令的参考文章，其中使用两个或更多指定的动态磁盘创建带区卷。
ms.topic: article
ms.assetid: 20dce735-5f7c-4f83-a580-d087e2913a00
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e9f0133783178002e35b32b665dc64dfb3144a19
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87891613"
---
# <a name="create-volume-stripe"></a>create volume stripe

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使用两个或更多指定的动态磁盘创建带区卷。 创建卷完成后，焦点会自动移到新卷。

## <a name="syntax"></a>语法

```
create volume stripe [size=<n>] disk=<n>,<n>[,<n>,...] [align=<n>] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- |  -----------|
| 大小 =`<n>` | 该卷将占用的每个磁盘上的磁盘空间量（以 MB 为单位）。 如果没有指定大小，新建卷将占据最小磁盘上的剩余可用空间以及其他磁盘上相同大小的空间。 |
| 磁盘 =`<n>,<n>[,<n>,...]` | 在其上创建带区卷的动态磁盘。 若要创建一个带区卷，需要至少两个动态磁盘。 `size=<n>`每个磁盘上分配的空间量等于。 |
| align =`<n>` | 将所有卷区与最接近的对齐边界对齐。 通常与硬件 RAID 逻辑单元号一起使用 (LUN) 阵列以提高性能。 `<n>`从磁盘开始到最接近的对齐边界 (KB) 的千字节数。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要创建大小为 1000 mb 的条带化卷，请在磁盘1和2上键入：

```
create volume stripe size=1000 disk=1,2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [create 命令](create.md)
