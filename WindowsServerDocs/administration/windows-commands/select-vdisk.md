---
title: select vdisk
description: '* * * * 的参考文章'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8808872a-3523-4205-a6c6-83fa738ee37a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 734b31d9c9bcf174bf4617418978935bc49ad6da
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936435"
---
# <a name="select-vdisk"></a>select vdisk

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

选择指定的虚拟硬盘 \( VHD \) ，并将焦点移到它上面。

> [!NOTE]
> 此命令仅适用于 Windows 7 和 Windows Server 2008 R2。

## <a name="syntax"></a>语法

```
select vdisk file=<full path> [noerr]
```

### <a name="parameters"></a>参数

|参数|说明|
|-------|--------|
|文件\=<full path>|指定现有 VHD 文件的完整路径和文件名。|
|noerr|仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="examples"></a>示例
若要将焦点转移到名为 "Test" 的 VHD，请键入：

```
select vdisk file=c:\test\test.vhd
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

-   [附加 vdisk](attach-vdisk.md)

-   [compact vdisk](compact-vdisk.md)



-   [分离 vdisk](detach-vdisk.md)

-   [detail vdisk](detail-vdisk.md)

-   [expand vdisk](expand-vdisk.md)

-   [Merge vdisk](merge-vdisk.md)

-   [list_1](list_1.md)


