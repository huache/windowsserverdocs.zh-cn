---
title: 模拟还原
description: 适用于模拟还原的参考主题，该主题测试编写器在计算机上的还原会话中参与，而不向编写器发出 PreRestore 或 PostRestore 事件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d883d94c-3cb1-4848-9d74-1b4378044b31
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1bab6c56cddc1d2ac95dc70205b0990b82fbfd12
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82721781"
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