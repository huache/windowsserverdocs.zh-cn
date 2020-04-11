---
title: bitsadmin setmaxdownloadtime
description: 适用于**bitsadmin setmaxdownloadtime**的 Windows 命令主题，用于设置下载超时（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 16b96cf1-5738-415c-9b9d-c4ea8d5e4fec
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f07931dfb9fabaec272384dced6d60f1335b6a94
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122912"
---
# <a name="bitsadmin-setmaxdownloadtime"></a>bitsadmin setmaxdownloadtime

设置下载超时（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /setmaxdownloadtime <job> <timeout>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| timeout | 下载超时的长度（以秒为单位）。 |

## <a name="examples"></a>示例

下面的示例将名为*myDownloadJob*的作业的超时值设置为10秒。

```
C:\>bitsadmin /setmaxdownloadtime myDownloadJob 10
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)