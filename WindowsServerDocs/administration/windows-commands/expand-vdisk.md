---
title: expand vdisk
description: 扩展 vdisk 命令的参考文章，可将虚拟硬盘（VHD）扩展到指定大小。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ae547b4-3813-4b86-bacd-bc273c028a2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a7951d4875249e46d850883f7863262774dd9bab
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932306"
---
# <a name="expand-vdisk"></a>expand vdisk

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将虚拟硬盘（VHD）扩展到指定大小。

必须选择并分离 VHD，此操作才能成功。 使用 "[选择 vdisk" 命令](select-vdisk.md)选择卷并将焦点移动到该卷。

## <a name="syntax"></a>语法

```
expand vdisk maximum=<n>
```

### <a name="parameters"></a>参数

 | 参数 | 说明 |
 |---------- | ----------- |
 | 最大值 =`<n>` | 指定 VHD 的新大小（以兆字节（MB）为单位）。 |

### <a name="examples"></a>示例

若要将所选 VHD 扩展到 20 GB，请键入：

```
expand vdisk maximum=20000
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [选择 vdisk 命令](select-vdisk.md)

- [附加 vdisk 命令](attach-vdisk.md)

- [compact vdisk 命令](compact-vdisk.md)

- [分离 vdisk 命令](detach-vdisk.md)

- [detail vdisk 命令](detail-vdisk.md)

- [merge vdisk 命令](merge-vdisk.md)

- [list 命令](list.md)
