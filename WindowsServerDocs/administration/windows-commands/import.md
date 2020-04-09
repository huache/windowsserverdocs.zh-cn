---
title: 导入
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7bd78d76-0560-4d47-944c-fe960be2c10b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 07fdd03c73c454e92218a4c6983eac7f29b50883
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80842170"
---
# <a name="import"></a>导入



将已加载的元数据文件中的可传送影子副本导入到系统中。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
import
```

## <a name="remarks"></a>备注

-   可传送的卷影副本不会立即存储在系统中。 它们的详细信息存储在备份组件文档 XML 文件中，该文件是 DiskShadow 自动请求并保存在工作目录中的 .cab 元数据文件中。 您可以使用 "**设置元数据**" 命令来更改此文件的路径和名称。
-   在可以使用**import**之前，必须使用**load Metadata**命令加载 DiskShadow 元数据文件。

## <a name="examples"></a><a name=BKMK_examples></a>示例

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