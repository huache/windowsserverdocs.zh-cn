---
title: perfmon
description: 用于在特定独立模式下启动 Windows 可靠性和性能监视器的 perfmon 命令的参考文章。
ms.topic: reference
ms.assetid: 9a8d5eca-8473-463e-a6e0-7bbd590b18e1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/25/2018
ms.openlocfilehash: c68f0c2160621ed38ea013697f178ec461c8d44c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627442"
---
# <a name="perfmon"></a>perfmon

在特定独立模式下启动 Windows 可靠性和性能监视器。

## <a name="syntax"></a>语法

```
perfmon </res|report|rel|sys>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /res | 启动资源视图。 |
| /report | 启动系统诊断数据收集器集，并显示结果报表。 |
| /rel | 启动可靠性监视器。 |
| /sys | 启动性能监视器。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [Windows 性能监视器](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc749154(v%3dws.11))
