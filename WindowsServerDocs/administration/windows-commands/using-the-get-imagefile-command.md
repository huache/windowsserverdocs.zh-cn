---
title: get-ImageFile
description: 获取-ImageFile 的参考文章，用于检索有关 Windows 映像（.wim）文件中包含的映像的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e1e296fb-20cf-4a60-9db4-4cbac7d4dab5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 127b5282b74020f002c7ccc55663fc2571584582
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85932219"
---
# <a name="get-imagefile"></a>get-ImageFile

检索有关 Windows 映像（.wim）文件中包含的映像的信息。

## <a name="syntax"></a>语法

```
WDSUTIL [Options] /Get-ImageFile /ImageFile:<wim file path> [/Detailed]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|像素\<WIM file path>|指定 .wim 文件的完整路径和文件名。|
|[/Detailed]|返回每个映像中的所有图像元数据。 如果未使用此选项，则默认行为是只返回映像名称、说明和文件名。|

## <a name="examples"></a>示例

若要查看有关映像的信息，请键入：
```
WDSUTIL /Get-ImageFile /ImageFile:C:\temp\install.wim
```
若要查看详细信息，请键入：
```
WDSUTIL /Verbose /Get-ImageFile /ImageFile:\\Server\Share\My Folder \install.wim /Detailed
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)