---
title: verbose
description: 详细的参考文章，其中显示指定命令的详细输出。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fcf30ae7-818f-4e7e-a083-a1812682032b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 079e441ba4a932e23493e7e37fbe36cab4c4971f
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85935244"
---
# <a name="verbose"></a>verbose

显示指定命令的详细输出。 可以将 **/verbose**与运行的任何其他 WDSUTIL 命令一起使用。 请注意，必须在**WDSUTIL**之后直接指定 **/verbose**和 **/progress** 。

## <a name="syntax"></a>语法

```
WDSUTIL /verbose <commands>
```

## <a name="examples"></a>示例

若要从自动添加数据库中删除已批准的计算机并显示详细输出，请键入：
```
WDSUTIL /Verbose /progress /Delete-AutoAddDevices /Server:MyWDSServer /DeviceType:ApprovedDevices
```