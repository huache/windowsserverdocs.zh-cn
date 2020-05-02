---
title: msdt
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ead1b672-a120-4e16-94aa-a8e13602c1d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e5d31b1b5a73d975aec08d675aaff04ee29c7d3c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723876"
---
# <a name="msdt"></a>msdt



在命令行或自动脚本中调用疑难解答包，并启用其他选项，无需用户输入。

## <a name="syntax"></a>语法

```
msdt </id <name> | /path <name> | /cab < name>> <</parameter> [options] … <parameter> [options]>>
```

### <a name="parameters"></a>参数

下表包括了 msdt 支持的参数和选项。


|      参数      |                                                                                            描述                                                                                             |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /id \<包名称> |        指定要运行的诊断包。 有关可用包的列表，请参阅本主题后面的 "可用疑难解答包" 部分中的疑难解答包 ID。         |
|  /path \<目录  |                                                                                           diagpkg 文件                                                                                            |
|   /dci \<密钥>   |                                        预填充以 msdt 为密钥字段。 仅当支持提供程序提供了密钥时，才使用此参数。                                         |
|  /dt \<目录>   | 显示指定目录中的故障排除历史记录。 诊断结果存储在用户的 **%LOCALAPPDATA%\Diagnostics**或 **%LOCALAPPDATA%\ElevatedDiagnostics**目录中。 |
| /af \<应答文件>  |                                               指定 XML 格式的应答文件，该文件包含对一个或多个诊断交互的响应。                                               |

