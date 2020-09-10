---
title: ksetup server
description: Ksetup 服务器命令的参考文章，可用于为运行 Windows 操作系统的计算机指定名称，因此 ksetup 命令所做的更改将更新目标计算机。
ms.topic: reference
ms.assetid: e3407111-ac92-457f-aa1f-a04fe9109d59
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4be82315bc0d683b5399350c618aa87e615067ba
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639576"
---
# <a name="ksetup-server"></a>ksetup server

允许你为运行 Windows 操作系统的计算机指定名称，因此 **ksetup** 命令所做的更改将更新目标计算机。

目标服务器名称存储在下的注册表中 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\LSA\Kerberos` 。 当你运行 **ksetup** 命令时，不会报告此项。

> [!IMPORTANT]
> 无法删除目标服务器名称。 相反，你可以将其更改回本地计算机名称，这是默认值。

## <a name="syntax"></a>语法

```
ksetup /server <servername>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<servername>` | 指定配置将在其上生效的完整计算机名称，例如 *IPops897.corp.contoso.com*。<p>如果指定了不完整的完全限定的域计算机名称，则该命令将失败。 |

### <a name="examples"></a>示例

若要使 **ksetup** 配置在 *IPops897* 计算机上生效（该计算机连接在 Contoso 域中），请键入：

```
ksetup /server IPops897.corp.contoso.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ksetup 命令](ksetup.md)
