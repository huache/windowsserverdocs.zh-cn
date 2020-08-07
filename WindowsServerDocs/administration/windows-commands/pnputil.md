---
title: pnputil
description: Pnputil 命令的参考文章，其中添加了驱动程序包，删除驱动程序包，并使用 pnputil.exe 实用程序列出了驱动程序存储区中的驱动程序包。
ms.topic: article
ms.assetid: fab686b8-09d3-4f6c-afa2-630e6036f44c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 4bd4a5ed4dcadb1011dfbf28647ba4f223249a34
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884919"
---
# <a name="pnputil"></a>pnputil

Pnputil.exe 是一种命令行实用工具，可用于管理驱动程序存储区。 你可以使用此命令添加驱动程序包、删除驱动程序包，以及列出存储中的驱动程序包。

## <a name="syntax"></a>语法

```
pnputil.exe [-f | -i] [ -? | -a | -d | -e ] <INF name>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|--|--|
| -a | 指定添加标识的 INF 文件。 |
| -d | 指定删除标识的 INF 文件。 |
| -E | 指定枚举所有第三方 INF 文件。 |
| -f | 指定强制删除标识的 INF 文件。 不能与 **– i**参数一起使用。 |
| -i | 指定安装标识的 INF 文件。 不能与 **-f**参数一起使用。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

添加名为 USBCAM 的 INF 文件。INF，键入：

```
pnputil.exe -a a:\usbcam\USBCAM.INF
```

若要添加所有 INF 文件（位于 c:\drivers 中），请键入：

```
pnputil.exe -a c:\drivers\*.inf
```

添加并安装 USBCAM。INF 驱动程序，请键入：

```
pnputil.exe -i -a a:\usbcam\USBCAM.INF
```

若要枚举所有第三方驱动程序，请键入：

```
pnputil.exe –e
```

若要删除名为为 oem0.inf 的 INF 文件和驱动程序，请键入：

```
pnputil.exe -d oem0.inf
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [popd 命令](popd.md)
