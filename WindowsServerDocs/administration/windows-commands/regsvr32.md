---
title: regsvr32
description: 用于在注册表中将 .dll 文件注册为命令组件的 regsvr32 命令的参考文章。
ms.topic: reference
ms.assetid: 3345e964-7d3e-42b8-abeb-42ed6edfe2b2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 670953ecb5de087d660c2d3b1b504e7301245b96
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639847"
---
# <a name="regsvr32"></a>regsvr32

将 .dll 文件注册为注册表中的命令组件。

## <a name="syntax"></a>语法

```
regsvr32 [/u] [/s] [/n] [/i[:cmdline]] <Dllname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /U | 注销服务器。 |
| /s | 禁止显示消息。 |
| /n | 阻止调用 **DllRegisterServer**。 此参数要求您同时使用 **/i** 参数。 |
| /i`<cmdline>` | 将可选的命令行字符串 (*cmdline*) 传递到 **DllInstall**。 如果将此参数与 **/u** 参数一起使用，则它将调用 **DllUninstall**。 |
| `<Dllname>` | 要注册的 .dll 文件的名称。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要为 Active Directory 架构注册 .dll，请键入：

```
regsvr32 schmmgmt.dll
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
