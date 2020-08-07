---
title: reset
description: '* * * * 的参考文章'
ms.topic: article
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f491a3d8c805ac6b3558f3778f6eba91a7551b82
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87883652"
---
# <a name="reset"></a>reset



将 DiskShadow.exe 重置为默认状态。 在分隔复合 DiskShadow 操作（如**创建**、**导入**、**备份**或**还原**）时，**重置**特别有用。

## <a name="syntax"></a>语法

```
reset
```

## <a name="remarks"></a>备注

-   使用**reset**命令时，**将**会丢失诸如 add、 **set**、 **load**或**writer**这样的命令的状态。 **Reset**还会释放 IVssBackupComponent 接口，并丢失非持久卷影副本。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)