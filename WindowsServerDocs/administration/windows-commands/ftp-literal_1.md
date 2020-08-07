---
title: ftp literal
description: Ftp 文本命令的参考文章，可将原义参数发送到远程 ftp 服务器。
ms.topic: article
ms.assetid: fb81aa2d-07fa-4e79-bf44-1fb5526fdf14
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bafa2626481941b91d501e4fd6df52aa1f8f05d1
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87889359"
---
# <a name="ftp-literal"></a>ftp literal

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将原义参数发送到远程 ftp 服务器。 返回单个 ftp 答复代码。

> [!NOTE]
> 此命令与 " [ftp 引号" 命令](ftp-quote.md)相同。

## <a name="syntax"></a>语法

```
literal <argument> [ ]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
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

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
