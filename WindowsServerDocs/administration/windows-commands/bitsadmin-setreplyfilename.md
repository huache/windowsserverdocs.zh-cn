---
title: bitsadmin setreplyfilename
description: Bitsadmin setreplyfilename 命令的参考文章，其中指定了包含服务器上传答复的文件的路径。
ms.topic: reference
ms.assetid: c26d3342-0533-40b1-a13e-e09678232b25
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e517b3b09e287d4364763b433e3209bf8d4794d6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630642"
---
# <a name="bitsadmin-setreplyfilename"></a>bitsadmin setreplyfilename

指定包含服务器上传答复的文件的路径。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /setreplyfilename <job> <file_path>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| file_path | 要放置服务器上传的位置-回复。 |

## <a name="examples"></a>示例

若要设置名为 *myDownloadJob*的作业的上传-答复文件名文件路径，请执行以下操作：

```
bitsadmin /setreplyfilename myDownloadJob c:\upload-reply
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
