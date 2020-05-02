---
title: create
description: Create 的参考主题，它使用当前上下文和选项设置启动卷影复制创建过程。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 837aa449-9b60-41ae-9ef1-ef67af6e5918
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cfddbebd5744d8cd222d67e46690ce8b5d2e0fde
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716839"
---
# <a name="create"></a>create

使用当前上下文和选项设置启动卷影复制创建过程。 卷影副本集中至少需要一个卷。

## <a name="syntax"></a>语法

```
create
```

## <a name="remarks"></a>备注

-   必须至少添加一个包含**add volume**命令的卷，然后才能使用**create**命令。
-   您可以使用 "**开始备份**" 命令来指定完整备份，而不是复制备份。
-   运行**create**命令后，可以使用**exec**命令从卷影副本运行用于备份的重复脚本。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)