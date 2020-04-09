---
title: 创建
description: 用于创建的 Windows 命令主题，该主题使用当前上下文和选项设置启动卷影复制创建过程。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 837aa449-9b60-41ae-9ef1-ef67af6e5918
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4d29285517ca678a15828079c95663fc4d501eaf
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846830"
---
# <a name="create"></a>创建

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