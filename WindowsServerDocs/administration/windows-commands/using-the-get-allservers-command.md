---
title: AllServers
description: AllServers 的参考文章，用于检索有关所有 Windows 部署服务服务器的信息。
ms.topic: reference
ms.assetid: fe2e3c69-8f2e-457d-af55-d249ebf70f53
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b60fb7710699c4fff6656a0e2a34684a538b116d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626351"
---
# <a name="get-allservers"></a>AllServers

检索有关所有 Windows 部署服务服务器的信息。

> [!NOTE]
> 如果你的环境中有许多 Windows 部署服务服务器，或者如果链接服务器的网络连接速度较慢，则此命令可能需要很长时间才能完成。

## <a name="syntax"></a>语法

```
WDSUTIL [Options] /Get-AllServers /Show:{Config | Images | All} [/Detailed] [/Forest:{Yes | No}]
```

### <a name="parameters"></a>参数

|   参数   |                                                                                                                 说明                                                                                                                  |
|---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Show： {Config |                                                                                                                    映像                                                                                                                    |
|  [/Detailed]  | 与 **/show： Images** 或 **/show： All**结合使用时，将返回每个映像中的所有映像元数据。 如果未指定 **/Detailed** 选项，则默认行为是返回映像名称、说明和文件名。 |
| [/Forest： {Yes |                                                                                                                     No}]                                                                                                                     |

## <a name="examples"></a>示例

若要查看有关所有服务器的信息，请键入：
```
WDSUTIL /Get-AllServers /Show:Config
```
若要查看所有服务器的详细信息，请键入：
```
WDSUTIL /Verbose /Get-AllServers /Show:All /Detailed /Forest:Yes
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)