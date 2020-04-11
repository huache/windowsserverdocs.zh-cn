---
title: bitsadmin util 和 setieproxy
description: '**Bitsadmin util 和 setieproxy**的 Windows 命令主题，用于设置使用服务帐户传输文件时使用的代理设置。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e9f31ba-3070-4ffd-a94c-388c8d78f688
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2ebb33ff917ddd43bbc62413755ca28478ad5a95
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122520"
---
# <a name="bitsadmin-util-and-setieproxy"></a>bitsadmin util 和 setieproxy

设置使用服务帐户传输文件时使用的代理设置。 必须从提升的命令提示符运行此命令，才能成功完成此命令。

> [!NOTE]
> BITS 1.5 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /util /setieproxy <account> <usage> [/conn <connectionname>]
```

### <a name="parameters"></a>参数


| 参数 | 说明 |
| --------- | ---------- |
| 帐户 | 指定要定义其代理设置的服务帐户。 可能的值包括：<ul><li>LOCALSYSTEM</li><li>   NETWORKSERVICE</li><li>LOCALSERVICE.</li></ul> |
| usage | 指定要使用的代理检测的形式。 可能的值包括：<ul><li>**NO_PROXY。** 不要使用代理服务器。</li><li>**检测.** 自动检测代理设置。</li><li>**MANUAL_PROXY。** 使用指定的代理列表和绕过列表。 必须紧跟在使用标记后指定列表。 例如， `MANUAL_PROXY proxy1,proxy2 NULL`。<ul><li>**代理列表。** 要使用的代理服务器的逗号分隔列表。</li><li>**绕过列表。** 不通过代理路由传输的主机名或 IP 地址的以空格分隔的列表。 这可以 \<本地 >，以指同一 LAN 上的所有服务器。 NULL 或的值可能用于空代理跳过列表。</li></ul><li>**AUTOSCRIPT.** 与自动**检测**相同，只不过它还运行脚本。 你必须在使用标记后紧跟指定脚本 URL。 例如， `AUTOSCRIPT http://server/proxy.js`。</li><li>**&.** 与**NO_PROXY**相同，不同之处在于删除手动代理 url （如果已指定）和使用自动检测发现的任何 url。</li></ul> |
| connectionname | 可选。 与 **/conn**参数一起使用，以指定要使用的调制解调器连接。 如果未指定 **/conn**参数，则 BITS 将使用 LAN 连接。 |

## <a name="remarks"></a>备注

使用此开关的每个连续调用都将替换以前指定的用法，但不会替换先前定义的用法的参数。 例如，如果在单独的调用上指定**NO_PROXY**、自动**检测**和**MANUAL_PROXY** ，则 BITS 将使用最后提供的使用情况，但保留以前定义的用法中的参数。

## <a name="examples"></a>示例

下面的示例设置了网络服务帐户的代理使用情况。

```
C:\>bitsadmin /Util /SetIEProxy localsystem AUTODETECT
```

下面是更多示例。

```
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1,proxy2,proxy3 NULL
```

```
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1:80
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)