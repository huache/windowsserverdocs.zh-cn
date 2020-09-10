---
title: 导入 diskpart
description: 用于将外部磁盘组导入到本地计算机的磁盘组中的 "导入" 命令的参考文章。
ms.topic: reference
ms.assetid: 4b9d2751-7637-4738-83b0-8c578eb28f27
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c20154e4f687aaaba5639baf4cbbbc6b536c72bd
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634509"
---
# <a name="import-diskpart"></a>import (diskpart)

将外部磁盘组导入到本地计算机的磁盘组。 此命令将导入与具有焦点的磁盘位于同一组中的每个磁盘。

> 无关紧要使用此命令之前，必须使用 " [选择磁盘" 命令](select-disk.md) 选择外部磁盘组中的动态磁盘，并将焦点移动到该磁盘。

## <a name="syntax"></a>语法

```
import [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

### <a name="examples"></a>示例

若要将具有焦点的磁盘所在磁盘组中的每个磁盘导入到本地计算机的磁盘组，请键入：

```
import
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [diskpart 命令](diskpart.md)
