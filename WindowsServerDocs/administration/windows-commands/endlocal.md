---
title: endlocal
description: Endlocal 命令的参考文章，该命令结束批处理文件中环境更改的本地化，并在运行相应的 setlocal 命令之前将环境变量还原到其值。
ms.topic: reference
ms.assetid: 765fae3c-0c0a-4639-99a4-cf613489b949
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 82fa050ef9f2ed35368a6eaf356c6aa6f70e5465
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030695"
---
# <a name="endlocal"></a>endlocal

结束批处理文件中环境更改的本地化，并在运行相应的 **setlocal** 命令之前将环境变量还原到其值。

## <a name="syntax"></a>语法

```
endlocal
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- **Endlocal**命令在脚本或批处理文件外不起作用。

- 批处理文件的末尾有一个隐式 **endlocal** 命令。

- 如果启用了命令扩展 () 默认情况下启用命令扩展，则 **endlocal** 命令会将命令扩展 (的状态恢复为已启用或已禁用的) ，直至运行相应的 **setlocal** 命令。

> [!NOTE]
> 有关启用和禁用命令扩展的详细信息，请参阅 [Cmd 命令](cmd.md)。

### <a name="examples"></a>示例

可以在批处理文件中本地化环境变量。 例如，以下程序启动网络上的 *superapp* 批处理程序，将输出定向到某个文件，并在记事本中显示该文件：

```
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
