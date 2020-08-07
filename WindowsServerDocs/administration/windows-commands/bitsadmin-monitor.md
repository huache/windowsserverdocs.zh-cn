---
title: bitsadmin monitor
description: 用于监视当前用户所拥有的传输队列中的作业的 bitsadmin monitor 命令的参考文章。
ms.topic: article
ms.assetid: 2c424d27-e011-49c2-b579-a2c235467c39
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3ba2cb315fb0696b8363506669aa41f1693bb758
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893668"
---
# <a name="bitsadmin-monitor"></a>bitsadmin monitor

监视当前用户拥有的传输队列中的作业。

## <a name="syntax"></a>语法

```
bitsadmin /monitor [/allusers] [/refresh <seconds>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| /allusers | 可选。 监视所有用户的作业。 您必须具有管理员特权才能使用此参数。 |
| /refresh | 可选。 按指定的时间间隔刷新数据 `<seconds>` 。 默认刷新间隔为5秒。 若要停止刷新，请按 CTRL + C。 |

## <a name="examples"></a>示例

监视当前用户拥有的作业的传输队列，每60秒刷新一次信息。

```
bitsadmin /monitor /refresh 60
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
