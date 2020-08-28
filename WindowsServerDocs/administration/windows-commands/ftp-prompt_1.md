---
title: ftp prompt
description: Ftp prompt 命令的参考文章，用于切换提示模式。
ms.topic: reference
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4d337e01c3e1bfe93d15c65f0885ec8e7e9dfee2
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023871"
---
# <a name="ftp-prompt"></a>ftp prompt

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

打开和关闭提示模式。 默认情况下，提示模式处于开启状态。 如果提示模式处于打开状态，则在多个文件传输过程中，ftp 命令会提示您有选择地检索或存储文件。

> [!NOTE]
> 当提示模式关闭时，可以使用 [ftp mget](ftp-mget.md) 和 [ftp mput](ftp-mput_1.md) 命令传输所有文件。

## <a name="syntax"></a>语法

```
prompt
```

### <a name="examples"></a>示例

若要打开和关闭提示模式，请键入：

```
prompt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
