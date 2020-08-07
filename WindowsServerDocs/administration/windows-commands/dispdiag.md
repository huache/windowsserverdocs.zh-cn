---
title: dispdiag
description: Dispdiag 命令的参考文章，它将显示信息记录到文件中。
ms.topic: article
ms.assetid: 5079e1dd-b57c-44ed-970f-e6b409369e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 78b8080395fa30a934d1a9380bf86beae7e62dc0
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890830"
---
# <a name="dispdiag"></a>dispdiag

日志向文件显示信息。

## <a name="syntax"></a>语法

```
dispdiag [-testacpi] [-d] [-delay <seconds>] [-out <filepath>]
```

#### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| - testacpi | 运行热键诊断测试。 显示测试期间按下的任何键的键名称、代码和扫描代码。 |
| -d | 生成包含测试结果的转储文件。 |
| -延迟`<seconds>` | 按指定时间 *（以秒为单位）* 延迟收集数据。 |
| -out`<filepath>`  | 指定用于保存所收集数据的路径和文件名。 这必须是最后一个参数。 |
| -? | 显示可用的命令参数，并提供使用它们的帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
