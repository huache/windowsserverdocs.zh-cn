---
title: bitsadmin 缓存和删除
description: '**Bitsadmin 缓存和删除**的 Windows 命令主题，用于删除特定的缓存条目。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 22540273-55a5-46ea-869b-6df2aa6808a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0fd7f1db83a62dd9c1085d6afdcf509c1c3ac8cf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850940"
---
# <a name="bitsadmin-cache-and-delete"></a>bitsadmin 缓存和删除

删除特定的缓存条目。

## <a name="syntax"></a>语法

```
bitsadmin /cache /delete recordID
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| recordID | 与缓存项关联的 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例删除 RecordID 为 {6511FB02-E195-40A2-B595-E8E2F8F47702} 的缓存条目。

```
C:\>bitsadmin /cache /delete {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)