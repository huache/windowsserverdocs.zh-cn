---
title: list providers
description: 列出提供程序命令的参考文章，其中列出了当前在系统上注册的卷影复制提供程序。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 844b4036-c0b9-449d-8347-7d58ef9bf16d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 64996c7a85fa7ad20a5ffbb1c22ae3396820b676
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931802"
---
# <a name="list-providers"></a>list providers

列出当前在系统上注册的卷影复制提供程序。

## <a name="syntax"></a>语法

```
list providers
```

### <a name="examples"></a>示例

若要列出当前注册的卷影复制提供程序，请键入：

```
list providers
```

类似于以下内容的输出：

```
* ProviderID: {b5946137-7b9f-4925-af80-51abd60b20d5}
        Type: [1] VSS_PROV_SYSTEM
        Name: Microsoft Software Shadow Copy provider 1.0
        Version: 1.0.0.7
        CLSID: {65ee1dba-8ff4-4a58-ac1c-3470ee2f376a}
1 provider registered.
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)