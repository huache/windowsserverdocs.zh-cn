---
title: 使用 verbose 命令
description: 详细的参考文章，其中显示指定命令的详细输出。
ms.topic: reference
ms.assetid: fcf30ae7-818f-4e7e-a083-a1812682032b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a5c05590bbbb3f1b185a64d6b0081a3d230d6b41
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640457"
---
# <a name="using-the-verbose-command"></a>使用 verbose 命令

显示指定命令的详细输出。 可以将 **/verbose** 与运行的任何其他 WDSUTIL 命令一起使用。 请注意，必须在**WDSUTIL**之后直接指定 **/verbose**和 **/progress** 。

## <a name="syntax"></a>语法

```
WDSUTIL /verbose <commands>
```

## <a name="examples"></a>示例

若要从自动添加数据库中删除已批准的计算机并显示详细输出，请键入：

```
WDSUTIL /Verbose /progress /Delete-AutoAddDevices /Server:MyWDSServer /DeviceType:ApprovedDevices
```