---
title: bitsadmin setreplyfilename
description: Bitsadmin setreplyfilename 命令的参考文章，其中指定了包含服务器上传答复的文件的路径。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c26d3342-0533-40b1-a13e-e09678232b25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 45582035ed986e50129e894fbabaffde5b219548
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927569"
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

若要设置名为*myDownloadJob*的作业的上传-答复文件名文件路径，请执行以下操作：

```
bitsadmin /setreplyfilename myDownloadJob c:\upload-reply
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
