---
title: ftp 引号
description: Ftp quote 命令的参考主题，它将原义参数发送到远程 ftp 服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 87dd81d4feb6a5509a8609f5c479e3352d5fb7ea
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83820337"
---
# <a name="ftp-quote"></a>ftp 引号

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将原义参数发送到远程 ftp 服务器。 返回单个 ftp 答复代码。

> [!NOTE]
> 此命令与[ftp 文本命令](ftp-literal_1.md)相同。

## <a name="syntax"></a>语法

```
quote <argument>[ ]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<argument>` | 指定要发送到 ftp 服务器的参数。 |

### <a name="examples"></a>示例

若要向远程 ftp 服务器发送**quit**命令，请键入：

```
quote quit
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp 文本命令](ftp-literal_1.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))