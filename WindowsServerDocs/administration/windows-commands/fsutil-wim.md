---
ms.assetid: 6c6ff819-f349-4aea-b0be-1f637f631736
title: Fsutil wim
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: d4a8f2c008c1a28e498edb7726a8c209e91f41af
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843920"
---
# <a name="fsutil-wim"></a>Fsutil wim
>适用于: Windows Server (半年频道)、Windows Server 2016、Windows 10

提供用于发现和管理支持 Windows 映像（WIM）的文件的函数。

## <a name="syntax"></a>语法

```
fsutil wim [enumfiles] <drive name> <data source>
fsutil wim [enumwims] <drive name>
fsutil wim [queryfile] <filename>
fsutil wim [removewim] <drive name> <data source>
```

#### <a name="parameters"></a>参数

|参数|说明|
|-------------|---------------|
|enumfiles|枚举支持 WIM 的文件。|
|\<驱动器名称 >|指定驱动器名称。|
|\<数据源 >|指定数据源。|
|enumwims|枚举后备 WIM 文件。|
|queryfile|查询文件是否由 WIM 支持，如果是，则显示有关 WIM 文件的详细信息。|
|\<文件名 >|指定文件名。|
|removewim|从备份文件中删除 WIM。|




### <a name="examples"></a>示例

要从数据源0枚举驱动器 C：的文件，请键入：

```
fsutil wim enumfiles C: 0
```

若要枚举驱动器 C：的后备 WIM 文件，请键入：

```
fsutil wim enumwims C:
```

若要查看某个文件是否由 WIM 支持，请键入：

```
fsutil wim C:\Windows\Notepad.exe
```

若要从卷 C：和数据源2的备份文件中删除 WIM，请键入：

```
fsutil wim removewims C: 2
```

### <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)

[Fsutil](Fsutil.md)