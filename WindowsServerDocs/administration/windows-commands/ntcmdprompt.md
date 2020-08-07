---
title: ntcmdprompt
description: Ntcmdprompt 命令的参考文章，该命令运行命令解释器**Cmd.exe**，而不是**Command.com**，在运行终止并保持常驻 () TSR 后，或在从 MS-DOS 应用程序中启动命令提示符之后运行。
ms.topic: article
ms.assetid: 0063bdbb-dc2b-41c4-99ee-b011603aaa86
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 53ed39f0fd455314dc5ccd90f0286f6dfd35ea72
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87885303"
---
# <a name="ntcmdprompt"></a>ntcmdprompt

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

运行命令解释器**Cmd.exe**，而不是在运行 "**终止" 并**保持常驻 (TSR) 或在从 MS-DOS 应用程序中启动命令提示符之后运行。

## <a name="syntax"></a>语法

```
ntcmdprompt
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 当**Command.com**运行时， **Cmd.exe**的某些功能（如命令历史记录的**doskey**显示）将不可用。 如果希望在启动终止并保持常驻 (TSR 后运行**Cmd.exe**命令解释器) 或者从基于 MS-DOS 的应用程序中启动命令提示符，则可以使用**ntcmdprompt**命令。 但是，请记住，在**Cmd.exe**运行时，TSR 可能不可用。 可以在**配置**文件中包含**ntcmdprompt**命令，或在应用程序的程序信息文件中包含等效的自定义启动文件 (Pif) 。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
