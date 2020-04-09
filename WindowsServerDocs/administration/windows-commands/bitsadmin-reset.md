---
title: bitsadmin reset
description: 用于**bitsadmin reset**的 Windows 命令主题，用于取消当前用户拥有的传输队列中的所有作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e4f9d1d-072c-493f-8d7a-f6d713c3ef29
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed1dcf9bce06af527ffb5b6a79d76d860d78450c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849790"
---
# <a name="bitsadmin-reset"></a>bitsadmin reset

取消当前用户拥有的传输队列中的所有作业。 > 无法重置本地系统创建的作业。 相反，您必须是管理员并使用任务计划程序将此命令计划为使用本地系统凭据的任务。

> [!NOTE]
> 在 BITSAdmin 1.5 及更早版本中，如果你具有管理员权限，则/reset 开关将取消队列中的所有作业。 此外，不支持/allusers 选项。

## <a name="syntax"></a>语法

```
bitsadmin /reset [/allusers]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| /allusers | 可选。 取消当前用户拥有的队列中的所有作业。 您必须具有管理员特权才能使用此参数。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例取消当前用户在传输队列中的所有作业。

```
C:\>bitsadmin /reset
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)