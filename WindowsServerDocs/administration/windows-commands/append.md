---
title: append
description: 追加命令的参考文章，使程序可以打开指定目录中的数据文件，就像它们位于当前目录中一样。
ms.topic: reference
ms.assetid: 9c3fea20-9502-40ad-a442-7a927aad88eb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0002adabaa8c9cbd2235383d997c77670d33d522
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633469"
---
# <a name="append"></a>append

允许程序在指定的目录中打开数据文件，就好像这些文件位于当前目录中一样。 如果在没有参数的情况下使用，则 **append** 将显示附加的目录列表。

> [!NOTE]
> Windows 10 不支持此命令。

## <a name="syntax"></a>语法

```
append [[<drive>:]<path>[;...]] [/x[:on|:off]] [/path:[:on|:off] [/e]
append ;
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `[\<drive>:]<path>` | 指定要追加的驱动器和目录。 |
| /x：开启 | 将附加的目录应用于文件搜索和启动应用程序。 |
| /x： off | 仅将附加的目录应用于打开文件的请求。 **/X： off**选项是默认设置。 |
| /path： on | 将附加的目录应用到已指定路径的文件请求。 **/path： on** 是默认设置。 |
| /path： off | 关闭 **/path： on**的效果。 |
| /e | 将附加目录列表的副本存储在名为 APPEND 的环境变量中。 **/e** 只能在启动系统后首次使用 **append** 时使用。 |
| ; | 清除追加的目录列表。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要清除附加目录列表，请键入：

```
append ;
```

若要将追加目录的副本存储到名为 *append*的环境变量中，请键入：

```
append /e
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
