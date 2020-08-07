---
title: timeout
description: 超时的参考文章，用于在指定的秒数内暂停命令处理器。
ms.topic: article
ms.assetid: e26b4a84-0e30-46e1-aa10-0667b7d3cb4c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 90ba2da52f97ee603ce7992e4df135c1284c4070
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87881403"
---
# <a name="timeout"></a>timeout

在指定的秒数内暂停命令处理器。



## <a name="syntax"></a>语法

```
timeout /t <TimeoutInSeconds> [/nobreak]
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|/t\<TimeoutInSeconds>|指定在命令处理器继续处理之前，介于-1 和 99999) 之间的 (的小数位数。 值-1 会使计算机无限期等待击键。|
|/nobreak|指定忽略用户密钥笔划。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   **Timeout**命令通常在批处理文件中使用。
-   即使超时期限未过期，用户按键也会立即继续执行命令处理器。
-   与 "**睡眠**" 命令结合使用时，"**超时**" 类似于 "**暂停**" 命令。

## <a name="examples"></a>示例

若要将命令处理器暂停10秒，请键入：
```
timeout /t 10
```
若要将命令处理器暂停100秒并忽略任何击键，请键入：
```
timeout /t 100 /nobreak
```
若要在按下某个键之前无限期暂停命令处理器，请键入：
```
timeout /t -1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
