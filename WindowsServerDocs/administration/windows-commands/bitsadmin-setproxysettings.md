---
title: bitsadmin setproxysettings
description: 用于为指定作业设置代理设置的 bitsadmin setproxysettings 命令的参考文章。
ms.topic: article
ms.assetid: be8edb1b-614e-4d0b-a8f8-64b4bde3e64b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0fb4e8893aa4becac49e5837baef3148541136ff
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87892961"
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
| 绕过 | 当*Usage*参数设置为 OVERRIDE 时使用。 必须包含以空格分隔的主机名或 IP 地址的列表，或者两者，不通过代理路由传输。 这可以是 `<local>` 指同一 LAN 上的所有服务器。 NULL 的值可以用于空代理跳过列表。 |

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
