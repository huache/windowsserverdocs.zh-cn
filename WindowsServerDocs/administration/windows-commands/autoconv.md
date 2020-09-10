---
title: autoconv
description: Autoconv 命令的参考文章，可将文件分配表 (Fat) 和 Fat32 卷转换为 NTFS 文件系统。
ms.topic: reference
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: cddb1c3a9f4f172f4fe026400eaa65716e9f3d0e
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633009"
---
# <a name="autoconv"></a>autoconv

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在运行 **autochk** 后，将文件分配表 (Fat) 和 Fat32 卷转换为 NTFS 文件系统，从而使现有文件和目录在启动时保持不变。 转换为 NTFS 文件系统的卷无法转换回 Fat 或 Fat32。

> [!IMPORTANT]
> 不能从命令行运行 **autoconv** 。 如果通过 **convert.exe**设置，则此设置只能在启动时运行。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [autochk 命令](autochk.md)

- [转换命令](convert.md)
