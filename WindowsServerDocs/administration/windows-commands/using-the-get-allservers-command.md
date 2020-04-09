---
title: AllServers
description: 用于 AllServers 的 Windows 命令主题，它检索所有 Windows 部署服务服务器的相关信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fe2e3c69-8f2e-457d-af55-d249ebf70f53
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b400d5a2be69e8e89a05b233cc2e8f29bec848f6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80831210"
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
| /Show： {Config |                                                                                                                    图像                                                                                                                    |
|  [/Detailed]  | 与 **/show： Images**或 **/show： All**结合使用时，将返回每个映像中的所有映像元数据。 如果未指定 **/Detailed**选项，则默认行为是返回映像名称、说明和文件名。 |
| [/Forest： {Yes |                                                                                                                     No}]                                                                                                                     |

## <a name="examples"></a><a name=BKMK_examples></a>示例

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