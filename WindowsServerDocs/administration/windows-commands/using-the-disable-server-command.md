---
title: 禁用-服务器
description: 用于禁用 Windows 部署服务服务器的所有服务的禁用服务器的参考文章。
ms.topic: reference
ms.assetid: b69fcfe0-b744-4794-bc75-2c9218c0ba66
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ed8fafb9c35f54656ab4551876dc0461ea1a2c55
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622036"
---
# <a name="disable-server"></a>禁用-服务器

禁用 Windows 部署服务服务器的所有服务。

## <a name="syntax"></a>语法

```
WDSUTIL [Options] /Disable-Server [/Server:<Server name>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[/Server： \<Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|

## <a name="examples"></a>示例

若要禁用服务器，请运行下列操作之一：
```
WDSUTIL /Disable-Server
WDSUTIL /Verbose /Disable-Server /Server:MyWDSServer
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

