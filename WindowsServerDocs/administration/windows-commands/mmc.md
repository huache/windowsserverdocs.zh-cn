---
title: mmc
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7bfa4030-ce42-40fb-922f-2f5145a80872
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d143336db3369b3b319391967db879126d2fb29
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839440"
---
# <a name="mmc"></a>mmc

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

使用 mmc 命令行选项，您可以打开特定的**mmc**控制台，以作者模式打开**mmc** ，或指定打开32位或64位版本的**mmc** 。
## <a name="syntax"></a>语法
```
mmc <path>\<filename>.msc [/a] [/64] [/32]
```
#### <a name="parameters"></a>参数

|       参数        |                                                                                                 说明                                                                                                 |
|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <path>\\<filename>.msc |        启动**mmc**并打开保存的控制台。 需为保存的控制台文件指定完整的路径和文件名。 如果未指定控制台文件， **mmc**会打开一个新的控制台。         |
|           /a           |                                                               在作者模式下打开保存的控制台。  用于对保存的控制台进行更改。                                                                |
|          /64           |                         打开64位版本的**mmc** （mmc64）。 仅在运行的是 Microsoft 64 位操作系统并需要使用 64 位管理单元时才使用此选项。                          |
|          /32           | 打开32位版本的**mmc** （mmc32）。 运行 Microsoft 64 位操作系统时，如果仅有32位的管理单元，则可以通过使用此命令行选项打开 mmc 来运行32位管理单元。 |
|           /?           |                                                                                    在命令提示符下显示帮助。                                                                                     |

## <a name="remarks"></a>备注
- 使用 <path> **\\** <filename>**services.msc**命令行选项，你可以使用环境变量来创建不依赖于控制台文件的显式位置的命令行或快捷方式。 例如，如果控制台文件的路径位于系统文件夹（例如， **mmc c:\winnt\system32\ console_name**）中，则可以使用可扩展的数据字符串 **% systemroot%** 来指定位置（**mmc% systemroot% \ system32 \ console_name**）。 对组织中在各台计算机上工作的人员分配任务时，这可能会很有用。
- 使用此选项打开控制台时，使用 **/a**命令行选项，无论其默认模式如何，都将在作者模式下打开它们。 这不会永久更改文件的默认模式设置;如果省略此选项，mmc 将根据其默认模式设置打开控制台文件。
- 在作者模式下打开**mmc**或控制台文件后，可通过单击**控制台**菜单上的 "**打开**" 来打开任何现有控制台。
- 你可以使用命令行来创建用于打开**mmc**和保存的控制台的快捷方式。 命令行命令适用于 "**开始**" 菜单上的 "**运行**" 命令、"任何命令提示符" 窗口、"快捷方式" 或任何批处理文件或调用命令的程序。
  ## <a name="additional-references"></a>其他参考
- - [命令行语法项](command-line-syntax-key.md)

