---
title: erase
description: 擦除命令的参考主题，用于删除一个或多个文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 024a4d0f-8679-4e06-b46f-61fdaf5464bc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0ec812e9a455cc0060a3f0a6be4d0e7227821a0b
ms.sourcegitcommit: fad2ba64bbc13763772e21ed3eabd010f6a5da34
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/09/2020
ms.locfileid: "82992381"
---
# <a name="erase"></a>erase

删除一个或多个文件。 此命令执行与**del**命令相同的操作。

> [!WARNING]
> 如果使用 "**清除**" 从磁盘中删除文件，则无法检索该文件。

## <a name="syntax"></a>语法

```
erase [/p] [/f] [/s] [/q] [/a[:]<attributes>] <names>
del [/p] [/f] [/s] [/q] [/a[:]<attributes>] <names>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<names>` | 指定一个或多个文件或目录的列表。 通配符可用于删除多个文件。 如果指定了目录，则会删除该目录中的所有文件。 |
| /p | 删除指定文件之前提示确认。 |
| /f | 强制删除只读文件。 |
| /s | 删除当前目录和所有子目录中的指定文件。 显示要删除的文件的名称。 |
| /q | 指定安静模式。 不会提示您确认删除。 |
| /a [：]`<attributes>` | 基于以下文件属性删除文件：<ul><li>**r**只读文件</li><li>**h**隐藏文件</li><li>**我**不是内容索引文件</li><li>**s**系统文件</li><li>准备好存档**的文件**</li><li>**l**重新分析点</li><li>**-** 用作前缀，即 "not"</li></ul>. |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果使用`erase /p`命令，你将看到以下消息：

    `FileName, Delete (Y/N)?`

    若要确认删除，请按**Y**。若要取消删除并显示下一个文件名（如果指定了一组文件），请按**N**。若要停止**erase**命令，请按 CTRL + C。

- 如果禁用命令扩展， **/s**参数将显示找不到的任何文件的名称，而不是显示要删除的文件的名称。

- 如果在`<names>`参数中指定特定文件夹，则还将删除所有包含的文件。 例如，如果要删除*\work*文件夹中的所有文件，请键入：

  ```
  erase \work
  ```

- 您可以使用通配符（**&#42;** 和 **？**）一次删除多个文件。 但是，若要避免无意中删除文件，应慎重使用通配符。 例如，如果键入以下命令：

  ```
  erase *.*
  ```

  **Erase**命令显示以下提示：

  `Are you sure (Y/N)?`

  若要删除当前目录中的所有文件，请按**Y** ，然后按 enter。 若要取消删除，请按**N** ，然后按 enter。

  > [!NOTE]
  > 在将通配符用于**erase**命令之前，请使用与**dir**命令相同的通配符来列出所有要删除的文件。

## <a name="examples"></a>示例

若要删除驱动器 C 上名为 Test 的文件夹中的所有文件，请键入下列内容之一：

```
erase c:\test
erase c:\test\*.*
```

若要从当前目录中删除文件扩展名为 .bat 的所有文件，请键入：

```
erase *.bat
```

若要删除当前目录中的所有只读文件，请键入：

```
erase /a:r *.*
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
