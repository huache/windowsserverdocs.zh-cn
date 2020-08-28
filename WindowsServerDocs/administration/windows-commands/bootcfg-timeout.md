---
title: bootcfg timeout
description: 用于更改操作系统超时值的 bootcfg timeout 命令的参考文章。
ms.topic: reference
ms.assetid: aa858eac-2bb7-4a27-a9bc-3e4a6eb8b2c6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed3e94447dba6cb09be986c2c482a42e9d83fe22
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034345"
---
# <a name="bootcfg-timeout"></a>bootcfg timeout

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改操作系统超时值。

## <a name="syntax"></a>语法

```
bootcfg /timeout <timeoutvalue> [/s <computer> [/u <domain>\<user> /p <password>]]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `/timeout <timeoutvalue>` | 指定 [boot loader] 部分中的超时值。 `<timeoutvalue>`是在 NTLDR 加载默认值之前，用户必须从启动加载器屏幕中选择操作系统的秒数。 的有效范围 `<timeoutvalue>` 是0-999。 如果该值为0，则 NTLDR 会立即启动默认操作系统，而不显示启动加载程序屏幕。 |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u** 参数中指定的用户帐户的密码。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用 **bootcfg/timeout** 命令：

```
bootcfg /timeout 30
bootcfg /s srvmain /u maindom\hiropln /p p@ssW23 /timeout 50
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
