---
title: bitsadmin getdescription
description: 用于**bitsadmin getdescription**的 Windows 命令主题，它检索指定作业的说明。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f3974603-ebbe-4d31-8217-040fe2d90c85
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2ff1638cf634d76001042691fd890dfe41f9ae0b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850720"
---
# <a name="bitsadmin-getdescription"></a>bitsadmin getdescription

检索指定作业的说明。

## <a name="syntax"></a>语法

```
bitsadmin /getdescription <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将检索名为*myDownloadJob*的作业的说明。

```
C:\>bitsadmin /getdescription myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)