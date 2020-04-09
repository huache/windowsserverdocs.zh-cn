---
title: bitsadmin monitor
description: 用于监视当前用户所拥有的传输队列中的作业的**bitsadmin monitor**Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2c424d27-e011-49c2-b579-a2c235467c39
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bda268afd5fda24bba2afb04b32bac9cda9a05bb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850210"
---
# <a name="bitsadmin-monitor"></a>bitsadmin monitor

监视当前用户拥有的传输队列中的作业。

## <a name="syntax"></a>语法

```
bitsadmin /monitor [/allusers] [/refresh <seconds>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| /allusers | 可选。 监视所有用户的作业。 您必须具有管理员特权才能使用此参数。 |
| /refresh | 可选。 按 `<seconds>`指定的间隔刷新数据。 默认刷新间隔为5秒。 若要停止刷新，请按 CTRL + C。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

以下示例监视当前用户拥有的作业的传输队列，每60秒刷新一次信息。

```
C:\>bitsadmin /monitor /refresh 60
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)