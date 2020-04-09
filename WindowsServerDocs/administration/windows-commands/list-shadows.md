---
title: 列表阴影
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fe568423-00ae-4ede-a1e7-07977cb50ad1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e22b0006709e1cf6636ad6c2bcc18432f59b4d1a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841160"
---
# <a name="list-shadows"></a>列表阴影



列出系统上持久的和现有的非持久卷影副本。

## <a name="syntax"></a>语法

```
list shadows {all | set <SetID> | id <ShadowID>}
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|全部|列出所有卷影副本。|
|设置 \<SetID >|列出属于指定卷影副本集 ID 的卷影副本。|
|id \<ShadowID >|列出具有指定卷影副本 ID 的所有卷影副本。|

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)