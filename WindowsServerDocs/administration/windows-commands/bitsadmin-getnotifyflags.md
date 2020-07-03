---
title: bitsadmin getnotifyflags
description: 用于检索指定作业的通知标志的 bitsadmin getnotifyflags 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d4657e6c-8959-4db7-a4af-e73d3f80ecf8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0ea97c039f372a2211b1e2a6c640c4499a38dfe4
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926928"
---
# <a name="bitsadmin-getnotifyflags"></a>bitsadmin getnotifyflags

检索指定作业的通知标志。

## <a name="syntax"></a>语法

```
bitsadmin /getnotifyflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="remarks"></a>备注

作业可以包含以下一个或多个通知标志：

| Flag | 描述 |
| ----- | ----- |
| 0x001 | 生成该作业中的所有文件都已都转移时发生的事件。 |
| 为 0x002 | 生成一个事件时发生错误。 |
| 0x004 | 禁用通知。 |
| 0x008 | 生成在修改作业或使传输进度事件。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的通知标志：

```
bitsadmin /getnotifyflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
