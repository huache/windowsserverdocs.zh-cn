---
title: 导入 diskshadow
description: 导入命令的参考文章，其中导入的元数据文件中的可传送卷影副本导入到系统中。
ms.topic: reference
ms.assetid: 7bd78d76-0560-4d47-944c-fe960be2c10b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: bf86c069bf0f5de4d6fa773d319bdd75beeb93eb
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634520"
---
# <a name="import-diskshadow"></a>导入 (diskshadow) 

将已加载的元数据文件中的可传送影子副本导入到系统中。

> 无关紧要使用此命令之前，必须使用 [load metadata 命令](load-metadata.md) 加载 DiskShadow 元数据文件。

## <a name="syntax"></a>语法

```
import
```

#### <a name="remarks"></a>备注

- 可传送的卷影副本不会立即存储在系统中。 它们的详细信息存储在备份组件文档 XML 文件中，该文件是 DiskShadow 自动请求并保存在工作目录中的 .cab 元数据文件中。 使用 " [设置元数据" 命令](set-metadata.md) 可更改此 XML 文件的路径和名称。

## <a name="examples"></a>示例

下面是一个示例 DiskShadow 脚本，演示如何使用 **import** 命令：

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

- [diskshadow 命令](diskshadow.md)