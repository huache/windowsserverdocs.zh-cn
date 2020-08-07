---
title: ftp lcd
description: Ftp lcd 命令的参考文章，用于更改本地计算机上的工作目录。
ms.topic: article
ms.assetid: 60a25808-6abb-408b-8373-0bbdcd0994b4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5b2d555e0edb69ab11ef7ff9e7a233fb1c6fc0f2
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87889369"
---
# <a name="ftp-lcd"></a>ftp lcd

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改本地计算机上的工作目录。 默认情况下，工作目录是启动**ftp**命令的目录。

## <a name="syntax"></a>语法

```
lcd [<directory>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `[<directory>]` | 指定要更改的本地计算机上的目录。 如果未指定*目录*，则将当前工作目录更改为默认目录。 |

### <a name="examples"></a>示例

若要将本地计算机上的工作目录更改为*c:\dir1*，请键入：

```
lcd c:\dir1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
