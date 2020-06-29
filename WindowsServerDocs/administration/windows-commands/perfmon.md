---
title: perfmon
description: Perfmon 命令的参考主题，它在特定的独立模式下启动 Windows 可靠性和性能监视器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9a8d5eca-8473-463e-a6e0-7bbd590b18e1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/25/2018
ms.openlocfilehash: 96d1589dcd75814c37c2ad295cf60887eb07739c
ms.sourcegitcommit: 771db070a3a924c8265944e21bf9bd85350dd93c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2020
ms.locfileid: "85472473"
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

- [Windows 性能监视器](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749154(v%3dws.11))
