---
title: bitsadmin info
description: Windows 命令主题**bitsadmin 信息**，显示有关指定作业的摘要信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5c306677-0d64-41c0-8276-5bba7750cecb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b9d8b840e39620db01c44001d9cb7d593be2be5d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850340"
---
# <a name="bitsadmin-info"></a>bitsadmin info

显示有关指定作业的摘要信息。

## <a name="syntax"></a>语法

```
bitsadmin /info <job> [/verbose]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |
| /verbose | 可选。 提供有关每个作业的详细信息。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

以下示例检索有关名为*myDownloadJob*的作业的信息。

```
C:\>bitsadmin /info myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)