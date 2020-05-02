---
title: bitsadmin setproxysettings
description: Bitsadmin setproxysettings 命令的参考主题，用于设置指定作业的代理设置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: be8edb1b-614e-4d0b-a8f8-64b4bde3e64b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7f7c54b3081c85756735d921fb70f726ba60d833
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720493"
---
# <a name="bitsadmin-setproxysettings"></a>bitsadmin setproxysettings

设置指定作业的代理设置。

## <a name="syntax"></a>语法

```
bitsadmin /setproxysettings <job> <usage> [list] [bypass]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| usage | 设置代理的使用情况，包括：<ul><li>**预配置.** 使用所有者的 Internet Explorer 默认值。</li><li>**NO_PROXY。** 不要使用代理服务器。</li><li>**忽略.** 使用显式代理列表和绕过列表。 必须遵循代理列表和代理跳过信息。</li><li>**检测.** 自动检测代理设置。</li></ul> |
| list | 当*Usage*参数设置为 OVERRIDE 时使用。 必须包含要使用的代理服务器的逗号分隔列表。 |
| 绕过 | 当*Usage*参数设置为 OVERRIDE 时使用。 必须包含以空格分隔的主机名或 IP 地址的列表，或者两者，不通过代理路由传输。 这可以是`<local>`指同一 LAN 上的所有服务器。 NULL 的值可以用于空代理跳过列表。 |

## <a name="examples"></a>示例

若要使用名为*myDownloadJob*的作业的各种使用选项设置代理设置，请执行以下操作：

```
bitsadmin /setproxysettings myDownloadJob PRECONFIG
```

```
bitsadmin /setproxysettings myDownloadJob NO_PROXY
```
```
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1:80
```

```
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1,proxy2,proxy3 NULL
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
