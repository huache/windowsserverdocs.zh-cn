---
title: secedit：验证
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 9fb06354-f55a-4ca4-9fbc-9a872eb9b9cf
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: be7ae316a189203aa70769d1d37291f532166735
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635531"
---
# <a name="seceditvalidate"></a>secedit：验证



验证存储在安全模板中的安全设置 ( .inf 文件) 。

## <a name="syntax"></a>语法

```
Secedit /validate <configuration file name>

```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|配置文件名|必需。</br>指定将验证的安全模板的路径和文件名。|

## <a name="remarks"></a>备注

如果安全模板已损坏或设置不当，则验证这些模板可以帮助你。

将不会应用无效的安全模板。

日志文件将不会更新。

在 Windows Server 2008 中，已 `Secedit /refreshpolicy` 替换为 `gpupdate` 。 有关如何刷新安全设置的信息，请参阅 [Gpupdate](gpupdate.md)。

## <a name="examples"></a>示例

对安全模板执行回滚后，你想要验证回退 inf 文件 secRBKcontoso 是否有效。
```
Secedit /validate secRBKcontoso.inf
```

## <a name="additional-references"></a>其他参考

-   [Secedit:generaterollback](secedit-generaterollback.md)
-   [Secedit](secedit.md)
- [命令行语法项](command-line-syntax-key.md)