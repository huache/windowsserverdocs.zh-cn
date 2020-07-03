---
title: ftp literal
description: Ftp 文本命令的参考文章，可将原义参数发送到远程 ftp 服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fb81aa2d-07fa-4e79-bf44-1fb5526fdf14
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e71d80b5ddf8e3c92f810e295e21dee28376f03d
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85933144"
---
# <a name="ftp-literal"></a>ftp literal

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将原义参数发送到远程 ftp 服务器。 返回单个 ftp 答复代码。

> [!NOTE]
> 此命令与 " [ftp 引号" 命令](ftp-quote.md)相同。

## <a name="syntax"></a>语法

```
literal <argument> [ ]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<argument>` | 指定要发送到 ftp 服务器的参数。 |

### <a name="examples"></a>示例

若要向远程 ftp 服务器发送**quit**命令，请键入：

```
literal quit
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [ftp 引号命令](ftp-quote.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
