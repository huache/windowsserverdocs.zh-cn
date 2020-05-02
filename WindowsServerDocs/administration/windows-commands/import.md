---
title: 进口
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7bd78d76-0560-4d47-944c-fe960be2c10b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 72cbd6195de64a6a0a7f2c258e19b2d5eb1378b1
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724857"
---
# <a name="import"></a>进口



将已加载的元数据文件中的可传送影子副本导入到系统中。



## <a name="syntax"></a>语法

```
import
```

## <a name="remarks"></a>备注

-   可传送的卷影副本不会立即存储在系统中。 它们的详细信息存储在备份组件文档 XML 文件中，该文件是 DiskShadow 自动请求并保存在工作目录中的 .cab 元数据文件中。 您可以使用 "**设置元数据**" 命令来更改此文件的路径和名称。
-   在可以使用**import**之前，必须使用**load Metadata**命令加载 DiskShadow 元数据文件。

## <a name="examples"></a>示例

下面是一个示例 DiskShadow 脚本，演示如何使用**import**命令：
```
#Sample DiskShadow script demonstrating IMPORT
SET CONTEXT PERSISTENT
SET CONTEXT TRANSPORTABLE
SET METADATA transHWshadow_p.cab
#P: is the volume supported by the Hardware Shadow Copy provider
ADD VOLUME P:
CREATE
END BACKUP
#The (transportable) shadow copy is not in the system yet.
#You can reset or exit now if you wish.

LOAD METADATA transHWshadow_p.cab
IMPORT
#The shadow copy will now be loaded into the system.
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)