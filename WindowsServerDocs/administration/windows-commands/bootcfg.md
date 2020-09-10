---
title: bootcfg
description: Bootcfg 命令的参考文章，其中配置、查询或更改 Boot.ini 文件设置。
ms.topic: reference
ms.assetid: 3deb354c-5717-4066-bc79-b9323d559e44
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6f187015ab3c8cba18e34601faebc1637ecf7896
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630090"
---
# <a name="bootcfg"></a>bootcfg

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

配置、查询或更改 Boot.ini 文件设置。

## <a name="syntax"></a>语法

```
bootcfg <parameter> [arguments...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
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
