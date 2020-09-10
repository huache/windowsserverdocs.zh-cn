---
title: nslookup set class
description: 用于更改查询类的 nslookup set 类命令的参考文章。
ms.topic: reference
ms.assetid: ed826400-40da-42b6-b7f0-95db73790723
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5f4eb309c3972230247bf231b0e731e146d8159a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634033"
---
# <a name="nslookup-set-class"></a>nslookup set class

更改查询类。 类指定信息的协议组。

## <a name="syntax"></a>语法

```
set class=<class>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<class>` | 有效值包括：<ul><li>**在中：** 指定 Internet 类。 这是默认值。</li><li>**混乱：** 指定混乱的类。</li><li>**HESIOD：** 指定 MIT Athena Hesiod 类。</li><li>**任何：** 指定使用以前列出的任何值。</li></ul> |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
