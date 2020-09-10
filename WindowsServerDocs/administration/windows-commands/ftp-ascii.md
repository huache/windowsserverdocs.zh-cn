---
title: ftp ascii
description: Ftp ascii 命令的参考文章，它将文件传输类型设置为 ASCII。
ms.topic: reference
ms.assetid: 523be48e-eab0-4237-8fb5-ca222824f0b6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 75b7918451836c1cda67fe5b5f6d8d8d3b73fde0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638567"
---
# <a name="ftp-ascii"></a>ftp ascii

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将文件传输类型设置为 ASCII。 **Ftp**命令支持 ascii (默认) 和二进制图像文件传输类型，但我们建议在传输文本文件时使用 ascii。 在 ASCII 模式下，执行与网络标准字符集之间的字符转换。 例如，根据目标操作系统，将根据需要转换行尾字符。

## <a name="syntax"></a>语法

```
ascii
```

### <a name="examples"></a>示例

若要将文件传输类型设置为 ASCII，请键入：

```
ascii
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp binary 命令](ftp-binary.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
