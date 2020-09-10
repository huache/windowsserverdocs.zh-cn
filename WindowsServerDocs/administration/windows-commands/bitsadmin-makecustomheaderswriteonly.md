---
title: bitsadmin makecustomheaderswriteonly
description: Bitsadmin makecustomheaderswriteonly 命令的参考文章，可将作业的自定义 HTTP 标头设置为只写。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 0eee6cc2fd8c825f02f7e01750be743b10beb73e
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631481"
---
# <a name="bitsadmin-makecustomheaderswriteonly"></a>bitsadmin makecustomheaderswriteonly

将作业的自定义 HTTP 标头设置为只写。

> [!IMPORTANT]
> 此操作无法撤消。

## <a name="syntax"></a>语法

```
bitsadmin /makecustomheaderswriteonly <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要为名为 *myDownloadJob*的作业仅编写自定义 HTTP 标头：

```
bitsadmin /makecustomheaderswriteonly myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
