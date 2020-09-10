---
title: 使用进度命令
description: 有关进度的参考文章，其中显示命令运行时的进度。
ms.topic: reference
ms.assetid: 8ce5e77b-e13f-4ac3-948d-31770a6c7e25
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 51f127cd9d707652e43a5cae2a2e0bfd7a573b69
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640783"
---
# <a name="using-the-progress-command"></a>使用进度命令

显示命令运行时的进度。 可以将 **/progress** 与运行的任何其他 WDSUTIL 命令一起使用。 请注意，必须在**WDSUTIL**之后直接指定 **/verbose**和 **/progress** 。

## <a name="syntax"></a>语法

```
WDSUTIL /progress <commands>
```

## <a name="examples"></a>示例

若要初始化服务器并显示进度，请键入：
```
WDSUTIL /Verbose /Progress /Initialize-Server /Server:MyWDSServer /RemInst:C:\RemoteInstall
```