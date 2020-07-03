---
title: telnet send
description: 用于 telnet send 的参考文章，可将 telnet 命令发送到 telnet 服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c217abc-1182-466e-914c-1ff16755021b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 44a0415a3516fcb15cd292c9e4c9c0a4a18e5ad9
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85937369"
---
# <a name="telnet-send"></a>telnet：发送

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

向 telnet 服务器发送 telnet 命令。

## <a name="syntax"></a>语法
```
sen[d] {ao | ayt | brk | esc | ip | synch | <string>} [?]
```
#### <a name="parameters"></a>参数

| 参数 |                     说明                      |
|-----------|------------------------------------------------------|
|    ao     |       发送 telnet 命令中止输出。        |
|    ayt    |       发送 telnet 命令。       |
|    brk    |            发送 telnet 命令 brk。            |
|    esc    |      发送当前的 telnet 转义符。      |
|    ip     |     发送 telnet 命令中断进程。     |
|   synch   |           发送 telnet 命令同步。           |
| <string>  | 将键入的任何字符串发送到 telnet 服务器。 |
|     ?     |     显示与此命令相关联的帮助。      |

## <a name="examples"></a>示例
发送到 telnet 服务器。
```
sen ayt
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
