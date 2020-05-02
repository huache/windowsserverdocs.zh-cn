---
title: del
description: Del 的参考主题，用于删除一个或多个文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 346eede2-2085-44f5-9936-6877b5d5a833
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 703597ae422518a5b401b656ace0b4cd73418be8
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716744"
---
# <a name="del"></a>del

删除一个或多个文件。 此命令与**erase**命令相同。



## <a name="syntax"></a>语法

```
del [/p] [/f] [/s] [/q] [/a[:]<Attributes>] <Names>
erase [/p] [/f] [/s] [/q] [/a[:]<Attributes>] <Names>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<名称>|指定一个或多个文件或目录的列表。 通配符可用于删除多个文件。 如果指定了目录，则会删除该目录中的所有文件。|
|/p|删除指定文件之前提示确认。|
|/f|强制删除只读文件。|
|/s|删除当前目录和所有子目录中的指定文件。 显示要删除的文件的名称。|
|/q|指定安静模式。 不会提示您确认删除。|
|/a [：]\<特性>|基于以下文件属性删除文件：</br>**r**只读文件</br>**h**隐藏文件</br>**我**不是内容索引文件</br>**s**系统文件</br>准备好存档**的文件**</br>**l**重新分析点</br>-前缀表示 "not"|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

> [!CAUTION]
> 如果使用**del**从磁盘中删除文件，则无法检索该文件。

-   如果使用 **/p**， **del**将显示文件的名称并发送以下消息：

    `FileName, Delete (Y/N)?`

    若要确认删除，请按 Y。若要取消删除并显示下一个文件名（即，如果指定了一组文件），请按 N。若要停止**del**命令，请按 CTRL + C。
- 如果禁用命令扩展， **/s**将显示找不到的任何文件的名称，而不是显示要删除的文件的名称（即，该行为是相反的）。
- 如果在 "*名称*" 中指定一个文件夹，则会删除该文件夹中的所有文件。 例如，以下命令将删除 \Work 文件夹中的所有文件：  
  ```
  del \work
  ```  
- 您可以使用通配符（**&#42;** 和 **？**）一次删除多个文件。 但是，若要避免无意中删除文件，应谨慎使用**del**命令。 例如，如果键入以下命令：  
  ```
  del *.*
  ```  
  **Del**命令显示以下提示：

  `Are you sure (Y/N)?`

  若要删除当前目录中的所有文件，请按 Y，然后按 ENTER。 若要取消删除，请按 N，然后按 ENTER。

> [!NOTE]
> 在将通配符用于**del**命令之前，请使用与**dir**命令相同的通配符来列出所有要删除的文件。

-   可从恢复控制台获取带有不同参数的**del**命令。

## <a name="examples"></a>示例

若要删除驱动器 C 上名为 Test 的文件夹中的所有文件，请键入下列内容之一：
```
del c:\test
del c:\test\*.*
```
若要从当前目录中删除文件扩展名为 .bat 的所有文件，请键入：
```
del *.bat
```
若要删除当前目录中的所有只读文件，请键入：
```
del /a:r *.*
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
