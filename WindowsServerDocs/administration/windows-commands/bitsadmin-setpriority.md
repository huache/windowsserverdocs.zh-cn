---
title: bitsadmin setpriority
description: 适用于**bitsadmin setpriority**的 Windows 命令主题，用于设置指定作业的优先级。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9348680a61649b938267b3277de9aa5aa521361f
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122760"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority

设置指定作业的优先级。

## <a name="syntax"></a>语法

```
bitsadmin /setpriority <job> <priority>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| priority | 设置作业的优先级，包括：<ul><li>FOREGROUND</li><li>HIGH</li><li>NORMAL</li><li>LOW</li></ul> |

## <a name="examples"></a>示例

下面的示例将名为*myDownloadJob*的作业的优先级设置为 normal。

```
C:\>bitsadmin /setpriority myDownloadJob NORMAL
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)