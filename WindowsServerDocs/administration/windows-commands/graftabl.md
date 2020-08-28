---
title: graftabl
description: Graftabl 命令的参考文章，Windows 操作系统可在图形模式下显示扩展字符集。
ms.topic: reference
ms.assetid: b08351d4-3d24-490c-86f6-1252da11d923
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8b92cc0501b69127bb8dd9e3faba5591a48542ea
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89035485"
---
# <a name="graftabl"></a>graftabl

使 Windows 操作系统能够在图形模式下显示扩展字符集。 如果在没有参数的情况下使用，则 **graftabl** 将显示前一个和当前代码页。

## <a name="syntax"></a>语法

```
graftabl <codepage>
graftabl /status
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<codepage>` | 指定一个代码页，用于定义图形模式下扩展字符的外观。 有效的代码页标识号为：<ul><li>**437** -美国</li><li>**850** -多语言 (拉丁语 I) </li><li>**852** -斯拉夫 (拉丁语 II) </li><li>**855** -西里尔文 (俄语) </li><li>**857** -土耳其语</li><li>**860** -葡萄牙语</li><li>**861** -冰岛语</li><li>**863** -加拿大-法语</li><li>**865** -北欧</li><li>**866** -俄语</li><li>**869** -现代希腊语</li></ul> |
| /status | 显示此命令所使用的当前代码页。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- **Graftabl**命令仅影响指定的代码页的扩展字符的监视器显示。 它不会更改实际的控制台输入代码页。 若要更改控制台输入代码页，请使用 [模式](mode.md) 或 [chcp](chcp.md) 命令。

- 每个退出代码及其简要说明：

    | 退出代码 | 说明 |
    | --------- | ----------- |
    | 0 | 已成功加载字符集。 未加载上一个代码页。 |
    | 1 | 指定的参数不正确。 未采取任何操作。 |
    | 2 | 出现文件错误。 |

- 可以在批处理程序中使用 ERRORLEVEL 环境变量来处理 **graftabl**返回的退出代码。

### <a name="examples"></a>示例

若要查看 **graftabl**使用的当前代码页，请键入：

```
graftabl /status
```

若要将代码页437的图形字符集加载 (美国) 到内存中，请键入：

```
graftabl 437
```

若要将代码页850的图形字符集加载 (多语言) 到内存中，请键入：

```
graftabl 850
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [freedisk 命令](freedisk.md)

- [mode 命令](mode.md)

- [chcp 命令](chcp.md)
