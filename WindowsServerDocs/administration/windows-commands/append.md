---
title: append
description: 用于 "**追加**" 的 Windows 命令主题，使程序可以打开指定目录中的数据文件，就像它们位于当前目录中一样。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9c3fea20-9502-40ad-a442-7a927aad88eb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 95bbc607ef297e7cf67da2e388884882356ef744
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851320"
---
# <a name="append"></a>append

允许程序在指定的目录中打开数据文件，就好像这些文件位于当前目录中一样。 如果在没有参数的情况下使用，则**append**将显示附加的目录列表。

> [!NOTE]
> Windows 10 不支持此命令。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
append [[<Drive>:]<Path>[;...]] [/x[:on|:off]] [/path:[:on|:off] [/e] 
append ;
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `[\<Drive>:]<Path>` | 指定要追加的驱动器和目录。 |
| `/x:on` | 将附加的目录应用于文件搜索和启动应用程序。 |
| `/x:off` | 仅将附加的目录应用于打开文件的请求。 **/X： off**选项是默认设置。 |
| `/path:on` | 将附加的目录应用到已指定路径的文件请求。 **/path： on**是默认设置。 |
| `/path:off` | 关闭 **/path： on**的效果。 |
| `/e` | 将附加目录列表的副本存储在名为 APPEND 的环境变量中。 **/e**只能在启动系统后首次使用**append**时使用。 |
| `;` | 清除追加的目录列表。 |
| `/?` | 在命令提示符下显示帮助。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要清除附加目录列表，请键入：

```
append ;
```

若要将追加目录的副本存储到名为 APPEND 的环境变量中，请键入：

```
append /e
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
