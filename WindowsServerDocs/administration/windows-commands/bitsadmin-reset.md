---
title: bitsadmin reset
description: Bitsadmin reset 命令的参考文章，用于取消当前用户拥有的传输队列中的所有作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0e4f9d1d-072c-493f-8d7a-f6d713c3ef29
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bc8faf10f991f06609d653c8cb7a1dc89de2fa8a
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926393"
---
# <a name="bitsadmin-reset"></a>bitsadmin reset

取消当前用户拥有的传输队列中的所有作业。 不能重置本地系统创建的作业。 相反，您必须是管理员并使用任务计划程序将此命令计划为使用本地系统凭据的任务。

> [!NOTE]
> 如果在 BITSAdmin 1.5 及更早版本中拥有管理员权限，则/reset 交换机将取消队列中的所有作业。 此外，不支持/allusers 选项。

## <a name="syntax"></a>语法

```
bitsadmin /reset [/allusers]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| /allusers | 可选。 取消当前用户拥有的队列中的所有作业。 您必须具有管理员特权才能使用此参数。 |

## <a name="examples"></a>示例

若为，则取消当前用户的传输队列中的所有作业。

```
bitsadmin /reset
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
