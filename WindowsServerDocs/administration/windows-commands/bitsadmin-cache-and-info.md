---
title: bitsadmin 缓存和信息
description: 适用于**bitsadmin 缓存**的 Windows 命令主题和用于转储特定缓存项的信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 15975cbf-dba6-49ca-a725-d15ce1952de5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3e9c6ce1eb972a76408483b8a27a3abca5500e56
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850890"
---
# <a name="bitsadmin-cache-and-info"></a>bitsadmin 缓存和信息

转储特定的缓存项。

## <a name="syntax"></a>语法

```
bitsadmin /cache /info recordID [/verbose]
```

### <a name="parameters"></a>参数

| Paramreter | 说明 |
| -------------- | -------------- |
| recordID | 与缓存项关联的 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例转储 recordID 值为 {6511FB02-E195-40A2-B595-E8E2F8F47702} 的缓存项。

```
C:\>bitsadmin /cache /info {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)