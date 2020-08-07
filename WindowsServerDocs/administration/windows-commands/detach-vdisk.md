---
title: detach vdisk
description: "\"分离 vdisk\" 命令的参考文章，用于停止所选虚拟硬盘 (VHD) 在主计算机上显示为本地硬盘驱动器。"
ms.topic: article
ms.assetid: 5f01dcb8-9237-4564-ad94-8a8dd0fd0cca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1efe62064a25d72eacf7175be287a32b7670e917
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87891326"
---
# <a name="detach-vdisk"></a>detach vdisk

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

停止所选虚拟硬盘 (VHD) 在主计算机上显示为本地硬盘驱动器。 分离 VHD 后，可以将其复制到其他位置。 在开始之前，必须选择 VHD 才能使此操作成功。 使用 "[选择 vdisk](select-vdisk.md) " 命令选择 VHD 并将焦点移动到该 VHD。


## <a name="syntax"></a>语法

```
detach vdisk [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

要分离所选 VHD，请键入：

```
detach vdisk
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [附加 vdisk 命令](attach-vdisk.md)

- [compact vdisk 命令](compact-vdisk.md)

- [detail vdisk 命令](detail-vdisk.md)

- [展开 vdisk 命令](expand-vdisk.md)

- [Merge vdisk 命令](merge-vdisk.md)

- [选择 vdisk 命令](select-vdisk.md)

- [list 命令](list.md)
