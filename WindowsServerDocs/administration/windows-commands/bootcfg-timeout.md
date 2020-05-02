---
title: bootcfg timeout
description: Bootcfg timeout 命令的参考主题，它更改操作系统超时值。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: aa858eac-2bb7-4a27-a9bc-3e4a6eb8b2c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e10ccab69ca58a6cef260546e965f90eecfc8beb
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82708947"
---
# <a name="bootcfg-timeout"></a>bootcfg timeout

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改操作系统超时值。

## <a name="syntax"></a>语法

```
bootcfg /timeout <timeoutvalue> [/s <computer> [/u <domain>\<user> /p <password>]]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `/timeout <timeoutvalue>` | 指定 [boot loader] 部分中的超时值。 `<timeoutvalue>`是在 NTLDR 加载默认值之前，用户必须从启动加载器屏幕中选择操作系统的秒数。 的有效范围`<timeoutvalue>`是0-999。 如果该值为0，则 NTLDR 会立即启动默认操作系统，而不显示启动加载程序屏幕。 |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址（请勿使用反斜杠）。 默认值为本地计算机。 |
| `/u <domain>\<user>`  | 使用`<user>`或`<domain>\<user>`指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用**bootcfg/timeout**命令：

```
bootcfg /timeout 30
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /timeout 50
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
