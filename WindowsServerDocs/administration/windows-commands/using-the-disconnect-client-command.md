---
title: 断开连接-客户端
description: 用于断开客户端与多播传输或命名空间断开连接的参考文章。
ms.topic: reference
ms.assetid: 876bbe6c-76ab-4de5-879b-d2066e700326
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 902d488a20391cb4317931aeb2572655d9aa291a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622013"
---
# <a name="disconnect-client"></a>断开连接-客户端

断开客户端与多播传输或命名空间的连接。 除非指定 **/force**，否则客户端将回退到其他传输方法 (如果客户端) 支持该方法。

## <a name="syntax"></a>语法

```
WDSUTIL /Disconnect-Client /ClientId:<Client ID> [/Server:<Server name>] [/Force]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|ClientId\<Client ID>|指定要断开连接的客户端的 ID。 若要查看客户端的 ID，请键入 **WDSUTIL/get-multicasttransmission/show：** client。|
|[/Server： \<Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名 (FQDN) 。 如果未指定服务器名称，则使用本地服务器。|
|/Force|完全停止安装，不使用回退方法。 请注意，Wdsmcast.exe 不支持任何回退机制。 如果未使用此选项，则默认行为如下所示：</br>-如果你使用的是 Windows 部署服务客户端，客户端将使用单播继续安装。</br>-如果使用的不是 Windows 部署服务客户端，则安装将失败。</br>重要提示：应慎用此选项，因为安装将失败，并且计算机可能处于不可用状态。|

## <a name="examples"></a>示例

若要断开客户端连接，请键入：
```
WDSUTIL /Disconnect-Client /ClientId:1
```
若要断开客户端的连接并强制安装失败，请键入：
```
WDSUTIL /Disconnect-Client /Server:MyWDSServer /ClientId:1 /Force
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)