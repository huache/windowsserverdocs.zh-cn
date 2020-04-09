---
title: lodctr
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5a849abd-6b31-4833-bc8a-306c05eca29a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 33c14970a669d24f1cc803003e8530712311c564
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840950"
---
# <a name="lodctr"></a>lodctr

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

允许你将性能计数器名称和注册表设置注册或保存到文件中，并指定受信任的服务。
## <a name="syntax"></a>语法
```
lodctr <filename> [/s:<filename>] [/r:<filename>] [/t:<servicename>]
```
#### <a name="parameters"></a>参数

|    参数     |                                                                                                                                         说明                                                                                                                                          |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    <filename>    |                                                                                          注册性能计数器名称设置，并说明初始化文件文件名中提供的文本。                                                                                          |
|  /s：<filename>   |                                                                                                       将性能计数器注册表设置和说明文本保存到文件 <filename>。                                                                                                       |
|        /r        |                                还原计数器注册表设置，并说明与注册表相关的当前注册表设置和缓存性能文件中的文本。<p>此选项仅在 Windows Server 2003 操作系统中可用。                                |
|  /r：<filename>   | 还原性能计数器注册表设置并说明文件 <filename>中的文本。 **警告：** 如果你使用**lodctr/r**命令，你将覆盖所有性能计数器注册表设置并说明文本，并将其替换为指定文件中定义的配置。 |
| /t：<servicename> |                                                                                                                       指示服务 <servicename> 受信任。                                                                                                                       |
|        /?        |                                                                                                                             在命令提示符下显示帮助。                                                                                                                             |

## <a name="remarks"></a>备注
如果提供的信息包含空格，请使用引号将文本括起来（例如 <filename>）。
## <a name="examples"></a><a name=BKMK_Examples></a>示例
若要将当前性能注册表设置和计数器说明文本保存到文件**性能备份 1**，请执行以下操作：
```
lodctr /s:perf backup1.txt
```
## <a name="additional-references"></a>其他参考
-   - [命令行语法项](command-line-syntax-key.md)

