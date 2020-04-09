---
title: bitsadmin list
description: '**Bitsadmin 列表**的 Windows 命令主题，其中列出了当前用户拥有的传输作业。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1416965e-e0e6-49cf-b1d4-b286d3cf8716
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1883da7bfa71a41952f6f67e25eca4dbbdd3353c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850320"
---
# <a name="bitsadmin-list"></a>bitsadmin list

列出当前用户拥有的传输作业。

## <a name="syntax"></a>语法

```
bitsadmin /list [/allusers][/verbose]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| /allusers | 可选。 列出所有用户的作业。 您必须具有管理员特权才能使用此参数。 |
| /verbose | 可选。 提供有关每个作业的详细信息。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索有关当前用户拥有的作业的信息。

```
C:\>bitsadmin /list
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)