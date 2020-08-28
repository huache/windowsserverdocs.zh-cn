---
title: ftp quote
description: Ftp quote 命令的参考文章，用于向远程 ftp 服务器发送原义参数。
ms.topic: reference
ms.assetid: 4500a1d3-c091-42c7-a909-f61df7f2e993
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5e70c93e7a8fe5c32038eec08c7115aa1fec80bf
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89035795"
---
# <a name="ftp-quote"></a>ftp quote

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将原义参数发送到远程 ftp 服务器。 返回单个 ftp 答复代码。

> [!NOTE]
> 此命令与 [ftp 文本命令](ftp-literal_1.md)相同。

## <a name="syntax"></a>语法

```
quote <argument>[ ]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<argument>` | 指定要发送到 ftp 服务器的参数。 |

### <a name="examples"></a>示例

若要向远程 ftp 服务器发送 **quit** 命令，请键入：

```
quote quit
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp 文本命令](ftp-literal_1.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
