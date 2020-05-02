---
title: detail volume
description: 详细信息卷的参考主题，其中显示了当前卷所在的磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 38f2bc75-2ed6-4e80-aa74-ab83133db1cd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2958c82b1dfc3b99d0e15690ef9857e7d83b244f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82719621"
---
# <a name="detail-volume"></a>detail volume

显示当前卷所在的磁盘。

## <a name="syntax"></a>语法

```
detail volume
```

## <a name="remarks"></a>备注

-   必须选择卷，此操作才能成功。 使用 "**选择音量**" 命令选择卷并将焦点移动到该卷。
-   卷详细信息不适用于只读卷，如 DVD-ROM 驱动器或 CD-ROM 驱动器。

## <a name="examples"></a>示例

若要查看当前卷所在的所有磁盘，请键入：
```
detail volume
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

