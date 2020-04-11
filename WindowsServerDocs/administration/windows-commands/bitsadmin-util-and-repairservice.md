---
title: bitsadmin util 和 repairservice
description: Windows 命令主题，适用于**bitsadmin util 和 repairservice**，用于修复各种版本的 BITS 服务中的已知问题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ac7baeb-4340-4186-bfcb-66478195378d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 164a402e7cbfc0a9223a97f4246eac84f0797aed
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81122519"
---
# <a name="bitsadmin-util-and-repairservice"></a>bitsadmin util 和 repairservice

如果 BITS 无法启动，此开关将尝试解析与错误的服务配置和 Windows 服务（如 LANManworkstation）和网络目录的依赖项相关的错误。 此开关还会生成一个输出，用于指示是否已解决问题。

> [!NOTE]
> BITS 1.5 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /util /repairservice [/force]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /force | 可选。 删除并重新创建该服务。|

> [!NOTE]
> 如果 BITS 再次创建该服务，则即使是在本地化的系统中，服务说明字符串也可能设置为 "英语"。

## <a name="examples"></a>示例

以下示例修复 BITS 服务配置。

```
C:\>bitsadmin /util /repairservice
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)