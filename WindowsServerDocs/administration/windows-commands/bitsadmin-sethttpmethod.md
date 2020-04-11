---
title: bitsadmin sethttpmethod
description: 适用于**bitsadmin sethttpmethod**的 Windows 命令主题，用于设置要使用的 HTTP 谓词。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: d349dcad7bdf6a6fc566ed961c3160836d7f49da
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122966"
---
# <a name="bitsadmin-sethttpmethod"></a>bitsadmin sethttpmethod

设置要使用的 HTTP 谓词。

## <a name="syntax"></a>语法

```
bitsadmin /sethttpmethod <job> <httpmethod>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| httpmethod | 要使用的 HTTP 谓词。 有关可用谓词的信息，请参阅[方法定义](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)