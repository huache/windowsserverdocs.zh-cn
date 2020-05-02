---
title: 脱机卷
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b8f7192f-ea38-47d0-9d4e-58ef68336ae6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d17295f3367fed054a7f6a245bae44ea3494a4a8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723454"
---
# <a name="offline-volume"></a>脱机卷



使具有焦点的联机卷进入脱机状态。

> [!IMPORTANT]
> 在任何版本的 Windows Vista 中，此 DiskPart 命令均不可用。

## <a name="syntax"></a>语法

```
offline volume [noerr]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|noerr|仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。|

## <a name="remarks"></a>备注

-   若要成功，必须选择卷。 使用 "**选择卷**" 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a>示例

若要使具有焦点的磁盘脱机，请键入：
```
offline volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

