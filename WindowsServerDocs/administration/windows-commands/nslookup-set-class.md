---
title: nslookup set class
description: 用于更改查询类的 nslookup set 类命令的参考文章。
ms.topic: article
ms.assetid: ed826400-40da-42b6-b7f0-95db73790723
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dbbcfa3dbdce653dc1318b69a33ba0bacbc2e359
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87885717"
---
# <a name="nslookup-set-class"></a>nslookup set class

更改查询类。 类指定信息的协议组。

## <a name="syntax"></a>语法

```
set class=<class>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<class>` | 有效值包括：<ul><li>**在中：** 指定 Internet 类。 这是默认值。</li><li>**混乱：** 指定混乱的类。</li><li>**HESIOD：** 指定 MIT Athena Hesiod 类。</li><li>**任何：** 指定使用以前列出的任何值。</li></ul> |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
