---
title: lodctr
description: Lodctr 命令的参考主题，可用于在文件中注册或保存性能计数器名称和注册表设置，并指定受信任的服务。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5a849abd-6b31-4833-bc8a-306c05eca29a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 221737d68280dabf34c270fccff02071ebf9b5a2
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820177"
---
# <a name="lodctr"></a>lodctr

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

允许你将性能计数器名称和注册表设置注册或保存到文件中，并指定受信任的服务。

## <a name="syntax"></a>语法

```
lodctr <filename> [/s:<filename>] [/r:<filename>] [/t:<servicename>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<filename>` | 指定用于注册性能计数器名称设置和说明性文本的初始化文件的名称。 |
| /s`<filename>` | 指定性能计数器注册表设置和说明性文本要保存到的文件的名称。 |
| /r | 从当前注册表设置和与注册表相关的缓存性能文件还原计数器注册表设置和说明性文本。 |
| /r`<filename>` | 指定还原性能计数器注册表设置和解释性文本的文件的名称。<p>**警告：** 如果使用此命令，你将覆盖所有性能计数器注册表设置和说明性文本，并将其替换为指定文件中定义的配置。 |
| /t:`<servicename>` | 指示服务 `<servicename>` 受信任。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果提供的信息包含空格，请使用引号将文本括起来（例如，"文件名 1"）。

### <a name="examples"></a>示例

若要将当前性能注册表设置和说明性文本保存到文件*性能备份 1*，请键入：

```
lodctr /s:perf backup1.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
