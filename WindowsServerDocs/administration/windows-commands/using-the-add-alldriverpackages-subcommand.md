---
title: 使用 AllDriverPackages 子命令
description: AllDriverPackages 的参考文章，用于将文件夹中存储的所有驱动程序包添加到服务器。
ms.topic: article
ms.assetid: ba6641c1-d7e9-43a9-9819-702dad5484ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 301842cce5306c8f7922660f49c9475fbbf70cc3
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87897038"
---
# <a name="add-alldriverpackages"></a>AllDriverPackages

将文件夹中存储的所有驱动程序包添加到服务器。

## <a name="syntax"></a>语法

```
WDSUTIL /Add-AllDriverPackages /FolderPath:<Folder Path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>]
```

### <a name="parameters"></a>参数

|          参数           |                                                              描述                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  FolderPath\<Folder Path>  |                      指定包含驱动程序包 .inf 文件的文件夹的完整路径。                      |
|   [/Server： \<Server name> ]   | 指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。 |
|     [/Architecture： {x86      |                                                                 ia64                                                                  |
| [/DriverGroup： \<Group Name> ] |                             指定应将包添加到其中的驱动程序组的名称。                             |

## <a name="examples"></a>示例

若要添加驱动程序包，请键入下列内容之一：
```
WDSUTIL /verbose /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers /Architecture:x86
```
```
WDSUTIL /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers\Printers /DriverGroup:Printer Drivers
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

[WdsDriverPackage](/previous-versions/windows/powershell-scripting/dn283440(v=wps.630))
