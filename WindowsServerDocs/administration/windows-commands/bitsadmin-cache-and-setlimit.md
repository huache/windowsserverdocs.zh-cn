---
title: bitsadmin 缓存和 setlimit
description: 适用于**bitsadmin 缓存和 setlimit**的 Windows 命令主题，用于设置缓存大小限制。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 746ee0b69da8f5bd22fec2ccbd432126cc25d94d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850870"
---
# <a name="bitsadmin-cache-and-setlimit"></a>bitsadmin 缓存和 setlimit

设置缓存大小限制。

## <a name="syntax"></a>语法

```
bitsadmin /cache /setlimit percent
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| % | 缓存限制定义为总硬盘空间的百分比。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将缓存大小限制为50%。

```
C:\>bitsadmin /cache /setlimit 50
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)