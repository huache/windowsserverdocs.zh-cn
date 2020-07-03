---
title: ftp lcd
description: Ftp lcd 命令的参考文章，用于更改本地计算机上的工作目录。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 60a25808-6abb-408b-8373-0bbdcd0994b4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7a325569717cb60ad0750447b2367ad18965d915
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927226"
---
# <a name="ftp-lcd"></a>ftp lcd

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改本地计算机上的工作目录。 默认情况下，工作目录是启动**ftp**命令的目录。

## <a name="syntax"></a>语法

```
lcd [<directory>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `[<directory>]` | 指定要更改的本地计算机上的目录。 如果未指定*目录*，则将当前工作目录更改为默认目录。 |

### <a name="examples"></a>示例

若要将本地计算机上的工作目录更改为*c:\dir1*，请键入：

```
lcd c:\dir1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
