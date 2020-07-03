---
title: simulate restore
description: 有关模拟还原的参考文章，可测试编写器在计算机上的还原会话中参与，而不向编写器发出 PreRestore 或 PostRestore 事件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d883d94c-3cb1-4848-9d74-1b4378044b31
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7cc247848ef4fac1e3a6537247f640f3533c2bcd
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936353"
---
# <a name="simulate-restore"></a>模拟还原

测试编写器参与计算机上的还原会话，而不向编写器发出**PreRestore**或**PostRestore**事件。

## <a name="syntax"></a>语法

```
simulate restore
```

## <a name="remarks"></a>备注

-   **模拟还原**用于测试编写器的还原是否成功。
-   在可以使用 "**模拟还原**" 之前，必须使用**加载元数据**命令加载 DiskShadow 元数据文件。 这将加载所选的编写器和组件以进行还原。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)