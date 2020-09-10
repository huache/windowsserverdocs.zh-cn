---
title: shift
description: 班次的参考文章，更改批处理文件中批处理参数的位置。
ms.topic: reference
ms.assetid: b56574e8-570a-4cc9-bbac-1b94fbf6a47a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0c4cff5e90542f44b4e2e163eacf2d3af6f8346a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640965"
---
# <a name="shift"></a>shift

更改批处理文件中批处理参数的位置。



## <a name="syntax"></a>语法

```
shift [/n <N>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/n \<N>|指定从第 *n*个参数开始移位，其中 *n* 是从0到8的任何值。 需要命令扩展，默认情况下已启用。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

- **移位**命令通过将每个参数复制到前一个参数来更改批参数 **%0**到 **%9**的值，将 **%1**的值复制到 **%0**，将 **%2**的值复制到 **%1**，依此类推。 这适用于写入对任意数量的参数执行相同操作的批处理文件。
- 如果启用了命令扩展，则 **shift** 命令支持 **/n** 命令行选项。 **/N**选项指定在第 n 个参数处开始移位，其中**n**是从0到8的任何值。 例如， **shift/2** 会将 **%3** 移位到% **2**， **%4** 转换为 **%3**，依此类推，并不影响 **%0** 和 **%1** 。 默认情况下启用命令扩展。
- 你可以使用 **shift** 命令创建一个可接受超过10个批处理参数的批处理文件。 如果在命令行中指定了10个以上的参数，则在第十个 (**%9**) 后出现的参数将一次移位到 **%9**中。
- **Shift**命令对 **%\*** 该批参数无效。
- 没有 **后退命令** 。 实现 **shift** 命令后，不能恢复在移位之前存在 (**%0**) 的批处理参数。

## <a name="examples"></a>示例

示例批处理文件中的以下行称为 Mycopy.bat 演示如何对任意数量的批处理参数使用 **shift** 。 在此示例中，Mycopy.bat 将文件列表复制到特定目录。 批处理参数由目录和文件名参数表示。
```
@echo off
rem MYCOPY.BAT copies any number of files
rem to a directory.
rem The command uses the following syntax:
rem mycopy dir file1 file2 ...
set todir=%1
:getfile
shift
if %1== goto end
copy %1 %todir%
goto getfile
:end
set todir=
echo All done
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
