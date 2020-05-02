---
title: recover
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: cf9be2e3-90c8-4773-a201-dc503b91948e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b316ed26f008a62f88aaeb4a7a7f3030d08f1588
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722616"
---
# <a name="recover"></a>recover



从错误或有缺陷的磁盘恢复可读的信息。



## <a name="syntax"></a>语法

```
recover [<Drive>:][<Path>]<FileName>
```

### <a name="parameters"></a>参数

|           参数           |                                          描述                                          |
|-------------------------------|-----------------------------------------------------------------------------------------------|
| [\<驱动器>：][<Path>]<FileName> | 指定要恢复的文件的位置和名称。 *FileName*是必需的。 |
|              /?               |                             在命令提示符下显示帮助。                              |

## <a name="remarks"></a>备注

-   **Recover**命令逐扇区读取文件，并从良好的扇区恢复数据。 坏扇区中的数据将丢失。
-   磁盘准备运行时， **chkdsk**报告的坏扇区被标记为 "错误"。 它们不会带来任何风险，**恢复**不会对其造成影响。
-   由于在您恢复文件时，坏扇区中的所有数据都将丢失，因此，一次只能恢复一个文件。
-   不能将通配符（**&#42;** 和 **？**）与**recover**命令一起使用。 如果文件不在当前目录中，则必须指定文件（以及文件的位置）。

## <a name="examples"></a>示例

若要在驱动器 D 上的 \Fiction 目录中恢复文件故事 .txt，请键入：
```
recover d:\fiction\story.txt 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)