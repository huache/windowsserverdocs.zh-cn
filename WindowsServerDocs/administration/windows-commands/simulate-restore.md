---
title: 模拟还原
description: 适用于模拟还原的 Windows 命令主题，该主题测试编写器对计算机上的还原会话的参与，而不向编写器发出 PreRestore 或 PostRestore 事件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d883d94c-3cb1-4848-9d74-1b4378044b31
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 024d654864c000e44bccb9ddb167c6147444cc00
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834100"
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