---
title: ftp 提示符
description: Ftp prompt 命令的参考主题，用于切换提示模式打开和关闭。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 930df39b-45c4-4e0b-bfe2-1d1963be817a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 57f0e1eead36665c19845944bf22325b1aecebbb
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820377"
---
# <a name="ftp-prompt"></a>ftp 提示符

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

打开和关闭提示模式。 默认情况下，提示模式处于开启状态。 如果提示模式处于打开状态，则在多个文件传输过程中，ftp 命令会提示您有选择地检索或存储文件。

> [!NOTE]
> 当提示模式关闭时，可以使用[ftp mget](ftp-mget.md)和[ftp mput](ftp-mput_1.md)命令传输所有文件。

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

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
