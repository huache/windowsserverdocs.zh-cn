---
title: ntcmdprompt
description: Ntcmdprompt 命令的参考文章，该命令运行命令解释器**Cmd.exe**，而不是**Command.com**，运行 "终止" 和 "保持驻留" （TSR）后，或在从 MS-DOS 应用程序中启动命令提示符之后运行。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0063bdbb-dc2b-41c4-99ee-b011603aaa86
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a70a8cfdbe6e37bfb8d90bed23e961d100843506
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85925344"
---
# <a name="ntcmdprompt"></a>ntcmdprompt

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

运行命令解释器**Cmd.exe**，而不是在运行 "终止并保持**驻留" （** TSR）后，或在从 MS-DOS 应用程序中启动命令提示符之后运行。

## <a name="syntax"></a>语法

```
ntcmdprompt
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 当**Command.com**运行时， **Cmd.exe**的某些功能（如命令历史记录的**doskey**显示）将不可用。 如果希望在启动终止和保持驻留（TSR）后或从基于 MS-DOS 的应用程序中启动命令提示符之后运行**Cmd.exe**命令解释器，则可以使用**ntcmdprompt**命令。 但是，请记住，在**Cmd.exe**运行时，TSR 可能不可用。 可以在**配置**文件中包含**ntcmdprompt**命令，也可以在应用程序的程序信息文件（Pif）中包含等效的自定义启动文件。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
