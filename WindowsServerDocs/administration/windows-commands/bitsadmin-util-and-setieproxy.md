---
title: bitsadmin util 和 setieproxy
description: Bitsadmin util 和 setieproxy 的 Windows 命令主题，用于设置使用服务帐户传输文件时使用的代理设置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e9f31ba-3070-4ffd-a94c-388c8d78f688
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4e7d8a9ff4e2388b61ee5ae00ae7afe421de68e6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848880"
---
# <a name="bitsadmin-util-and-setieproxy"></a>bitsadmin util 和 setieproxy

设置使用服务帐户传输文件时使用的代理设置。

**BITSAdmin 1.5 及更早版本**：不支持。

## <a name="syntax"></a>语法

```
bitsadmin /Util /SetIEProxy <Account> <Usage>[/Conn <ConnectionName>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|Account|指定要定义其代理设置的服务帐户的类型。 可能的值为：</br>-LOCALSYSTEM</br>-NETWORKSERVICE</br>-LOCALSERVICE|
|用法|指定要使用的代理检测的形式。 可能的值为：</br>-NO_PROXY-不使用代理服务器。</br>-自动检测-自动检测代理设置。</br>-MANUAL_PROXY-使用显式代理列表和绕过列表。 紧随用量标记，指定代理列表和跳过列表。 例如，MANUAL_PROXY proxy1，proxy2 为 NULL。</br>    -代理列表是要使用的代理服务器的逗号分隔列表。</br>    -旁路列表是以空格分隔的主机名或 IP 地址的列表，或者两者，不通过代理路由传输。 这可以 \<本地 >，以指同一 LAN 上的所有服务器。 NULL 或的值可能用于空代理跳过列表。</br>-AUTOSCRIPT-与自动检测相同，只不过它还执行脚本。 指定紧跟在用量标记后面的脚本 URL。 例如，AUTOSCRIPT http://server/proxy.js。</br>-RESET-与 NO_PROXY 相同，不同之处在于删除手动代理 Url （如果已指定）和使用自动检测发现的 Url。|
|ConnectionName|可选-与 **/Conn**参数结合使用，用于指定要使用的调制解调器连接。 如果未指定 **/Conn**参数，则 BITS 将使用 LAN 连接。 指定紧跟 **/Conn**参数的调制解调器连接名称。|

## <a name="remarks"></a>备注

使用此开关的每个连续调用都将替换以前指定的用法，而不是以前定义的用法的参数。 例如，如果在单独的调用上指定 NO_PROXY、自动检测和 MANUAL_PROXY，则 BITS 将使用最后提供的使用情况，但保留以前定义的用法中的参数。

> [!IMPORTANT]
> 必须从提升的命令提示符运行此命令，才能成功完成此命令。

## <a name="examples"></a>示例

下面的示例设置了网络服务帐户的代理使用情况。

```
C:\>bitsadmin /Util /SetIEProxy localsystem AUTODETECT
```

下面是更多示例。

```
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1,proxy2,proxy3 NULL
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1:80 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)