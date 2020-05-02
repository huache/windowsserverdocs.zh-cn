---
title: autoconv
description: Autoconv 命令的参考主题，它将文件分配表（Fat）和 Fat32 卷转换为 NTFS 文件系统。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ea8f55270435c6632be2e527569b4a4b4ca81136
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718776"
---
# <a name="autoconv"></a>autoconv

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在运行**autochk**后，将文件分配表（Fat）和 Fat32 卷转换为 NTFS 文件系统，以使现有文件和目录在启动时保持不变。 转换为 NTFS 文件系统的卷无法转换回 Fat 或 Fat32。

> [!IMPORTANT]
> 不能从命令行运行**autoconv** 。 如果是通过**convert**设置的，则此设置只能在启动时运行。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [autochk 命令](autochk.md)

- [转换命令](convert.md)
