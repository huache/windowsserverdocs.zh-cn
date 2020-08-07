---
title: nslookup finger
description: 用于在当前设备上连接到 finger 服务器的 nslookup finger 命令参考文章。
ms.topic: article
ms.assetid: 11ea2bde-8ccb-4b87-bbad-231dd9e5e858
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cd055ba9ad9049a5076020d5ec49a55b9dc12d15
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87885884"
---
# <a name="nslookup-finger"></a>nslookup/finger

与当前设备上的 finger 服务器连接。

## <a name="syntax"></a>语法

```
finger [<username>] [{[>] <filename> | [>>] <filename>}]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<username>` | 指定要查找的用户的名称。 |
| `<filename>` | 指定用于保存输出的文件名。 您可以使用大于 (`>`) 和双大于 (`>>`) 字符，以常规方式重定向输出。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
