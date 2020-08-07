---
title: bootcfg
description: Bootcfg 命令的参考文章，其中配置、查询或更改 Boot.ini 文件设置。
ms.topic: article
ms.assetid: 3deb354c-5717-4066-bc79-b9323d559e44
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: edab8bc0b4e63544282e53f0a7b6e1fc255a4be7
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880519"
---
# <a name="bootcfg"></a>bootcfg

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

配置、查询或更改 Boot.ini 文件设置。

## <a name="syntax"></a>语法

```
bootcfg <parameter> [arguments...]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| [bootcfg addsw](bootcfg-addsw.md) | 为指定的操作系统项添加操作系统加载选项。 |
| [bootcfg copy](bootcfg-copy.md) | 创建现有启动项的副本，您可以将命令行选项添加到该副本中。 |
| [bootcfg dbg1394](bootcfg-dbg1394.md) | 为指定的操作系统项配置1394端口调试。 |
| [bootcfg debug](bootcfg-debug.md) | 添加或更改指定操作系统项的调试设置。 |
| [bootcfg default](bootcfg-default.md) | 指定要指定为默认的操作系统项。 |
| [bootcfg delete](bootcfg-delete.md) | 删除 Boot.ini 文件的 [操作系统] 部分中的操作系统项。 |
| [bootcfg ems](bootcfg-ems.md) | 允许用户添加或更改用于将紧急管理服务控制台重定向到远程计算机的设置。 |
| [bootcfg query](bootcfg-query.md) | 查询并显示来自 Boot.ini 的 [启动加载器] 和 [操作系统] 部分条目。 |
| [bootcfg raw](bootcfg-raw.md) | 将指定为字符串的操作系统加载选项添加到 Boot.ini 文件的 [操作系统] 部分中的操作系统项。 |
| [bootcfg rmsw](bootcfg-rmsw.md) | 删除指定操作系统项的操作系统加载选项。 |
| [bootcfg timeout](bootcfg-timeout.md) | 更改操作系统超时值。 |
