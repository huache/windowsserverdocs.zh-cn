---
title: nslookup set class
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed826400-40da-42b6-b7f0-95db73790723
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc3bb4e36582f01584c0b89a12d43874322c3190
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838580"
---
# <a name="nslookup-set-class"></a>nslookup set class



更改查询类。 类指定信息的协议组。

## <a name="syntax"></a>语法

```
set class=<Class>
```

### <a name="parameters"></a>参数

| 参数 |                                                                                                                                    说明                                                                                                                                    |
|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| \<类 >  | 默认类为。 下面列出了此命令的有效值。</br>-IN：指定 Internet 类。</br>-混乱：指定混乱的类。</br>-HESIOD：指定 MIT Athena Hesiod 类。</br>-ANY：指定前面列出的任何通配符。 |
|   {帮助   |                                                                                                                                        ?}                                                                                                                                         |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)