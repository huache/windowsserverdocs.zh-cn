---
title: get-ImageFile
description: 获取-ImageFile 的参考文章，它检索有关 Windows 映像 ( .wim) 文件中包含的映像的信息。
ms.topic: article
ms.assetid: e1e296fb-20cf-4a60-9db4-4cbac7d4dab5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 10b86929366cc8734a5ff155200fb3078f0cd5d4
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87879375"
---
# <a name="get-imagefile"></a>get-ImageFile

检索有关 Windows 映像 ( .wim) 文件中包含的映像的信息。

## <a name="syntax"></a>语法

```
WDSUTIL [Options] /Get-ImageFile /ImageFile:<wim file path> [/Detailed]
```

### <a name="parameters"></a>参数

|参数|描述|
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