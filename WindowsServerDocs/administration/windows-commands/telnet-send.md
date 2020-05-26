---
title: telnet 发送
description: Telnet send 的参考主题，它将 telnet 命令发送到 telnet 服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c217abc-1182-466e-914c-1ff16755021b vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5dd4bf9828c4b71e7b2291dfd5d453c43679e059
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821067"
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
