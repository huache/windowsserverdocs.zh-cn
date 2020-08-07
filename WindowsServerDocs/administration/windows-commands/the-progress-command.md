---
title: 使用进度命令
description: 有关进度的参考文章，其中显示命令运行时的进度。
ms.topic: article
ms.assetid: 8ce5e77b-e13f-4ac3-948d-31770a6c7e25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9a970e5f547bd4b4f64dbae757ae7b61ca9aaf2b
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87881515"
---
# <a name="using-the-progress-command"></a>使用进度命令

显示命令运行时的进度。 可以将 **/progress**与运行的任何其他 WDSUTIL 命令一起使用。 请注意，必须在**WDSUTIL**之后直接指定 **/verbose**和 **/progress** 。

## <a name="syntax"></a>语法

```
WDSUTIL /progress <commands>
```

## <a name="examples"></a>示例

若要初始化服务器并显示进度，请键入：
```
WDSUTIL /Verbose /Progress /Initialize-Server /Server:MyWDSServer /RemInst:C:\RemoteInstall
```