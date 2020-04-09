---
title: autoconv
description: 适用于**autoconv**的 Windows 命令主题，它将文件分配表（Fat）和 Fat32 卷转换为 NTFS 文件系统。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fe0e388a1d4fd79567ef0562197e3181bbbc46f4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851110"
---
# <a name="autoconv"></a>autoconv

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

在运行**autochk**后，将文件分配表（Fat）和 Fat32 卷转换为 NTFS 文件系统，以使现有文件和目录在启动时保持不变。 转换为 NTFS 文件系统的卷无法转换回 Fat 或 Fat32。

## <a name="remarks"></a>备注

不能在命令行上运行**autoconv** 。 这只会在启动时运行，前提是通过**convert**进行设置。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [autochk](autochk.md)

- [convert](convert.md)

- [使用文件系统](https://go.microsoft.com/fwlink/?LinkId=4509)
