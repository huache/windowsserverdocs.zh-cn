---
title: 进口
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4b9d2751-7637-4738-83b0-8c578eb28f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 569d986c57ae8b3d7253c050146ac0583c7c92df
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724848"
---
# <a name="import"></a>进口



将外部磁盘组导入到本地计算机的磁盘组。

## <a name="syntax"></a>语法

```
import [noerr]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

-   导入命令将导入与具有焦点的磁盘位于同一组中的每个磁盘。
-   若要成功执行此操作，必须选择外部磁盘组中的动态磁盘。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a>示例

若要将具有焦点的磁盘所在磁盘组中的每个磁盘导入到本地计算机的磁盘组，请键入：
```
import
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

