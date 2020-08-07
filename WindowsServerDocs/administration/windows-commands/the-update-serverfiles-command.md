---
title: 更新-ServerFiles
description: ServerFiles 的参考文章，它使用存储在服务器的%Windir%\System32\RemInst 文件夹中的最新文件更新 REMINST 共享文件夹中的文件。
ms.topic: article
ms.assetid: 23aa79df-38c6-401e-91bd-cd23811b30b4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f60e5b5c5208d5718a287fd2d012368d13fad9f9
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87881466"
---
# <a name="update-serverfiles"></a>更新-ServerFiles

使用存储在服务器的%Windir%\System32\RemInst 文件夹中的最新文件更新 REMINST 共享文件夹中的文件。 若要确保 Windows 部署服务安装的有效性，应在每次服务器升级后运行此命令一次，Service Pack 安装或更新 Windows 部署服务文件。

## <a name="syntax"></a>语法

```
WDSUTIL [Options] /Update-ServerFiles [/Server:<Server name>]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|[/Server： \<Server name> ]|指定服务器的名称。 此名称可以是 NetBIOS 名称，也可以是完全限定的域名 (FQDN) 。 如果未指定服务器名称，将使用本地服务器。|

## <a name="examples"></a>示例

若要更新文件，请键入下列内容之一：
```
WDSUTIL /Update-ServerFiles
WDSUTIL /Verbose /Progress /Update-ServerFiles /Server:MyWDSServer
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)