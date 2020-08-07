---
title: CD
description: Cd 命令的参考文章，其中显示了或更改当前目录的名称。
ms.topic: article
ms.assetid: 932d9cc1-3dff-40da-835c-1cb0894874f1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 87766cd7be95eeb9cbecd29ec88a044224dc81da
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880383"
---
# <a name="cd"></a>CD

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

显示当前目录的名称或更改当前目录。 如果仅用于驱动器号 (例如， `cd C:`) ， **cd**将显示指定驱动器中当前目录的名称。 如果在没有参数的情况下使用， **cd**将显示当前驱动器和目录。

> [!NOTE]
> 此命令与[chdir 命令](chdir.md)相同。

## <a name="syntax"></a>语法

```
cd [/d] [<drive>:][<path>]
cd [..]
chdir [/d] [<drive>:][<path>]
chdir [..]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| /d | 更改当前驱动器以及驱动器的当前目录。 |
| `<drive>:` | 指定要显示或更改的驱动器 (（如果不同于当前驱动器) ）。 |
| `<path>` | 指定要显示或更改的目录的路径。 |
| [..] | 指定要更改为父文件夹。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="remarks"></a>备注

如果启用了命令扩展，则以下条件适用于**cd**命令：

- 当前目录字符串被转换为使用与磁盘上的名称相同的大小写。 例如， `cd c:\temp` 如果磁盘上出现这种情况，则会将当前目录设置为 C：\Temp。

- 空格不被视为分隔符，因此 `<path>` 可以包含空格而无需用引号引起来。 例如：

  ```
  cd username\programs\start menu
  ```

  相当于：

  ```
  cd "username\programs\start menu"
  ```

  如果禁用了扩展，则需要引号。

- 若要禁用命令扩展，请键入：

  ```
  cmd /e:off
  ```

## <a name="examples"></a>示例

若要返回根目录，请查看驱动器的目录层次结构顶部：

```
cd\
```

若要更改与你所在的驱动器不同的驱动器上的默认目录，请执行以下操作：

```
cd [<drive>:[<directory>]]
```

若要验证对目录所做的更改，请键入：

```
cd [<drive>:]
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [chdir 命令](chdir.md)
