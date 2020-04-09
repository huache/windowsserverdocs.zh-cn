---
title: 更新-ServerFiles
description: ServerFiles 的 Windows 命令主题，它使用存储在服务器的%Windir%\System32\RemInst 文件夹中的最新文件更新 REMINST 共享文件夹中的文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 23aa79df-38c6-401e-91bd-cd23811b30b4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 37cbb880246cf5e5ff6a9e007dbe720de8dd1cbe
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832950"
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
|[/Server：\<Server name >]|指定服务器的名称。 此名称可以是 NetBIOS 名称或完全限定的域名（FQDN）。 如果未指定服务器名称，将使用本地服务器。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要更新文件，请键入下列内容之一：
```
WDSUTIL /Update-ServerFiles
WDSUTIL /Verbose /Progress /Update-ServerFiles /Server:MyWDSServer
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)