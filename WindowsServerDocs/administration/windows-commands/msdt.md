---
title: msdt
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ead1b672-a120-4e16-94aa-a8e13602c1d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 87c1e4e8cd6d9de036b47de590867a6531d0335a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839250"
---
# <a name="msdt"></a>msdt



在命令行或自动脚本中调用疑难解答包，并启用其他选项，无需用户输入。

## <a name="syntax"></a>语法

```
msdt </id <name> | /path <name> | /cab < name>> <</parameter> [options] … <parameter> [options]>>
```

### <a name="parameters"></a>参数

下表包括了 msdt 支持的参数和选项。


|      参数      |                                                                                            说明                                                                                             |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /id \<包名称 > |        指定要运行的诊断包。 有关可用包的列表，请参阅本主题后面的 "可用疑难解答包" 部分中的疑难解答包 ID。         |
|  /path \<directory  |                                                                                           diagpkg 文件                                                                                            |
|   /dci \<密钥 >   |                                        预填充以 msdt 为密钥字段。 仅当支持提供程序提供了密钥时，才使用此参数。                                         |
|  /dt \<directory >   | 显示指定目录中的故障排除历史记录。 诊断结果存储在用户的 **%LOCALAPPDATA%\Diagnostics**或 **%LOCALAPPDATA%\ElevatedDiagnostics**目录中。 |
| /af \<应答文件 >  |                                               指定 XML 格式的应答文件，该文件包含对一个或多个诊断交互的响应。                                               |

