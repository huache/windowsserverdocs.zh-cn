---
title: bitsadmin util 和 getieproxy
description: 适用于 bitsadmin util 和 getieproxy 的 Windows 命令主题，它检索给定服务帐户的代理使用情况。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6d50c7e3-f4eb-4ca5-9f0c-4ed396087db6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d0d2a8634f3b42d655632a280cb9b998111c800b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848970"
---
# <a name="bitsadmin-util-and-getieproxy"></a>bitsadmin util 和 getieproxy

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

检索给定服务帐户的代理使用情况。

## <a name="syntax"></a>语法

```
bitsadmin /Util /GetIEProxy <Account> [/Conn <ConnectionName>]
```

### <a name="parameters"></a>参数

|参数|说明|
|-------|--------|
|Account|指定要检索其代理设置的服务帐户。 可能的值为：<p>-LOCALSYSTEM<br />-NETWORKSERVICE<br />-LOCALSERVICE|
|ConnectionName|可选，与 **/Conn**参数一起使用，以指定要使用的调制解调器连接。 如果未指定 **/Conn**参数，则 BITS 将使用 LAN 连接。 指定紧跟 **/Conn**参数的调制解调器连接名称。|

## <a name="remarks"></a>备注

此开关显示每个代理使用的值，而不仅仅是为服务帐户指定的代理使用情况。 有关设置服务帐户代理使用情况的详细信息，请参阅[bitsadmin util and setieproxy](bitsadmin-util-and-setieproxy.md)开关。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例显示了网络服务帐户的代理使用情况。

```
C:\>bitsadmin /Util /GetIEProxy NETWORKSERVICE
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
