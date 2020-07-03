---
title: merge vdisk
description: 用于将差异虚拟硬盘（VHD）与相应的父 VHD 合并的 merge vdisk 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5865bb08-89a3-406c-8328-0ef8868d03e8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 41201885861b7084fa7b49be8b5bf5a0e7394981
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925035"
---
# <a name="merge-vdisk"></a>merge vdisk

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将差异虚拟硬盘（VHD）与其对应的父 VHD 合并在一起。 父 VHD 将被修改以包括来自差异 VHD 的修改。 此命令修改父 VHD。 因此，依赖于父项的其他差异 Vhd 将不再有效。

> [!IMPORTANT]
> 您必须选择并分离 VHD 才能使此操作成功。 使用 "**选择 vdisk** " 命令选择 VHD 并将焦点移动到该 VHD。

## <a name="syntax"></a>语法

```
merge vdisk depth=<n>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 深度 =`<n>` | 指示要合并在一起的父 VHD 文件的数目。 例如， `depth=1` 指示差异 VHD 将与差异链的一个级别相合并。 |

### <a name="examples"></a>示例

若要将差异 VHD 与其父 VHD 合并，请键入：

```
merge vdisk depth=1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [附加 vdisk 命令](attach-vdisk.md)

- [compact vdisk 命令](compact-vdisk.md)

- [detail vdisk 命令](detail-vdisk.md)

- [分离 vdisk 命令](detach-vdisk.md)

- [展开 vdisk 命令](expand-vdisk.md)

- [选择 vdisk 命令](select-vdisk.md)

- [list 命令](list.md)
