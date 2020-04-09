---
title: pause
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: cab3afc3-d046-432f-a0bf-6282f0099032
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 135d074a71c7153cc1665ad7b543bdba56ed66e8
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837680"
---
# <a name="pause"></a>pause



暂停批处理程序的处理并显示以下提示：
```
Press any key to continue . . .
```
有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
pause
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

- 在运行**pause**命令时，将显示以下消息：  
  ```
  Press any key to continue . . .
  ```  
- 如果按 CTRL + C 停止批处理程序，将显示以下消息：  
  ```
  Terminate batch job (Y/N)?
  ```  
  如果按 "Y" （对于 "是"）来响应此消息，批处理程序将结束并控制返回到操作系统。
- 可以在可能不希望处理的批处理文件的一部分之前插入**pause**命令。 当**暂停暂停**批处理程序的处理时，可以按 CTRL + C，然后按 Y 停止批处理程序。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要创建一个批处理程序来提示用户更改其中一个驱动器中的磁盘，请键入：
```
@echo off 
:Begin 
copy a:*.* 
echo Put a new disk into drive A 
pause 
goto begin
```
在此示例中，驱动器 A 中的磁盘上的所有文件都复制到当前目录中。 在该消息提示你将新磁盘放入驱动器 A 后， **pause**命令将挂起处理，以便你可以更改磁盘，然后按任意键继续处理。 此批处理程序在无穷循环中运行- **goto begin**命令将命令解释器发送到批处理文件的开始标签。 若要停止此批处理程序，请按 CTRL + C，然后按 Y。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)