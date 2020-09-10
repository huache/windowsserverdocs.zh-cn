---
title: set_2
description: Set_2 的参考文章，用于设置用于创建卷影副本的上下文、选项、详细模式和元数据文件。
ms.topic: reference
ms.assetid: acf24663-1a50-4321-b48d-1717655e9476
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 685f66692e324b29bb0a33aaaefaec44b52b218d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639477"
---
# <a name="set_2"></a>set_2

设置用于创建卷影副本的上下文、选项、详细模式和元数据文件。 如果不使用参数，则 **set** 会列出所有当前设置。

## <a name="syntax"></a>语法

```
set
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
set verbose {on|off}
set metadata <MetaData.cab>
```

## <a name="set-sub-commands"></a>设置子命令

|子命令|说明|
|-----------|-----------|
|上下文|设置用于创建卷影副本的上下文。 请参阅设置语法和参数的 [上下文](set-context.md) 。|
|选项|设置创建卷影副本的选项。 有关语法和参数，请参阅 [Set 选项](set-option.md) 。|
|verbose|打开或关闭详细输出模式。 请参阅 [设置详细](set-verbose.md) 的语法和参数。|
|metadata|设置阴影创建元数据文件的名称和位置。 请参阅设置语法和参数的 [元数据](set-metadata.md) 。|
|/?|在命令提示符下显示帮助。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)