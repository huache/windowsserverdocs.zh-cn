---
title: 更新-ServerFiles
description: ServerFiles 的参考文章，它使用存储在服务器的%Windir%\System32\RemInst 文件夹中的最新文件更新 REMINST 共享文件夹中的文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 23aa79df-38c6-401e-91bd-cd23811b30b4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 79b9332d5962c7e3c50ea3d7c71f33111a0e74b8
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930131"
---
# <a name="update-serverfiles"></a>更新-ServerFiles

使用存储在服务器的%Windir%\System32\RemInst 文件夹中的最新文件更新 REMINST 共享文件夹中的文件。 若要确保 Windows 部署服务安装的有效性，应在每次服务器升级后运行此命令一次，Service Pack 安装或更新 Windows 部署服务文件。

## <a name="syntax"></a>语法

```
WDSUTIL [Options] /Update-ServerFiles [/Server:<Server name>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[/Server： \<Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|

## <a name="examples"></a>示例

若要更新文件，请键入下列内容之一：
```
WDSUTIL /Update-ServerFiles
WDSUTIL /Verbose /Progress /Update-ServerFiles /Server:MyWDSServer
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)