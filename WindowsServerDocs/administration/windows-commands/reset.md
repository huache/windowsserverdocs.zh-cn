---
title: reset
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5c27ddd93d06670a30f797bd58dd396a9e7ce70a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835780"
---
# <a name="reset"></a>reset



将 DiskShadow 重置为默认状态。 在分隔复合 DiskShadow 操作（如**创建**、**导入**、**备份**或**还原**）时，**重置**特别有用。

## <a name="syntax"></a>语法

```
reset
```

## <a name="remarks"></a>备注

-   使用**reset**命令时，**将**会丢失诸如 add、 **set**、 **load**或**writer**这样的命令的状态。 **Reset**还会释放 IVssBackupComponent 接口，并丢失非持久卷影副本。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)