---
title: 禁用-服务器
description: 用于禁用 Windows 部署服务服务器的所有服务的禁用服务器的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b69fcfe0-b744-4794-bc75-2c9218c0ba66
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 30b2593a9d2f83c70467fb58766e14b040931d5f
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933950"
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
|[/Server： \<Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|

## <a name="examples"></a>示例

若要禁用服务器，请运行下列操作之一：
```
WDSUTIL /Disable-Server
WDSUTIL /Verbose /Disable-Server /Server:MyWDSServer
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

