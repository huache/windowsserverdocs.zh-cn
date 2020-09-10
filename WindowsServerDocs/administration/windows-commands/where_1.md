---
title: where
description: Where 的参考文章，其中显示了与给定搜索模式匹配的文件的位置。
ms.topic: reference
ms.assetid: 0b3486a5-896b-4d92-84b8-e463a0b76487
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 683f467e3f023e7f859bb7543e1a3feef17ce294
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641223"
---
# <a name="where"></a>where



显示与给定的搜索模式匹配的文件的位置。



## <a name="syntax"></a>语法

```
where [/r <Dir>] [/q] [/f] [/t] [$<ENV>:|<Path>:]<Pattern>[ ...]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/r \<Dir>|指示从指定目录开始的递归搜索。|
|/q|返回退出代码 (**0** 表示成功， **1** 表示失败) ，而不显示匹配文件的列表。|
|/f|用引号显示 **where** 命令的结果。|
|/t |显示文件大小以及每个匹配文件的上次修改日期和时间。|
|[$\<ENV>:\|\<Path>:]\<Pattern>[ ...]|指定要匹配的文件的搜索模式。 至少需要一种模式，并且模式可以包含通配符字符 (**&#42;** 和 **？**) 。 默认 **情况下，搜索** 当前目录和 PATH 环境变量中指定的路径。 你可以通过使用格式 $*ENV*：*pattern* (来指定要搜索的其他路径，其中 *ENV* 是包含一个或多个路径) 或使用格式 *路径*：*pattern* (其中 *path* 是你要在其) 搜索的目录路径的现有环境变量。 这些可选格式不应与 **/r** 命令行选项一起使用。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   如果不指定文件扩展名，则默认情况下，PATHEXT 环境变量中列出的扩展名将追加到该模式。
-   **其中** ，可以运行递归搜索，显示文件信息（如日期或大小），并接受环境变量来代替本地计算机上的路径。

## <a name="examples"></a>示例

若要在当前计算机及其子目录的驱动器 C 中查找名为 Test 的所有文件，请键入：
```
where /r c:\ test
```
若要列出公共目录中的所有文件，请键入：
```
where $public:*.*
```
若要在远程计算机、Computer1 及其子目录的驱动器 C 中查找名为 Notepad 的所有文件，请键入：
```
where /r \\computer1\c notepad.*
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)