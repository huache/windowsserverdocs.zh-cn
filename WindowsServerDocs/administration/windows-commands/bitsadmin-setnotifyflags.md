---
title: bitsadmin setnotifyflags
description: 适用于**bitsadmin setnotifyflags**的 Windows 命令主题，用于设置指定作业的事件通知标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 73c088ce2bae8d2ad99b313417c14449ddd822b5
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122791"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

设置指定作业的事件通知标志。

## <a name="syntax"></a>语法

```
bitsadmin /setnotifyflags <job> <notifyflags>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| notifyflags | 可以包含以下一个或多个通知标志，其中包括：<ul><li>**1.** 当作业中的所有文件都已传输时生成事件。</li><li>**2.** 发生错误时生成事件。</li><li>**3.** 在所有文件完成传输或发生错误时生成事件。</li><li>**4.** 禁用通知。</li></ul> |

## <a name="examples"></a>示例

下面的示例设置通知标志，以便在发生错误时为名为*myDownloadJob*的作业生成事件。

```
C:\>bitsadmin /setnotifyflags myDownloadJob 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)