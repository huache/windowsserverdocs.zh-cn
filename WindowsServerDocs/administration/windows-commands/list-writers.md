---
title: list writers
description: 用于列出系统上的编写器的列表编写器命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1c30cbc4-f568-4fa7-b564-66c41d3ca82d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a3b4334d9f1f1a76b390a29a1b9cfd877da91185
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931773"
---
# <a name="list-writers"></a>list writers

列出系统上的编写器。 如果在没有参数的情况下使用，则默认情况下， **list**显示**列表元数据**的输出。

## <a name="syntax"></a>语法

```
list writers [metadata | detailed | status]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| metadata | 列出编写器的标识和状态，并显示元数据（如组件详细信息和排除的文件）。 这是默认参数。 |
| 详情 | 列出与**元数据**相同的信息，但还包括所有组件的完整文件列表。 |
| 状态 | 仅列出已注册编写器的标识和状态。 |

### <a name="examples"></a>示例

若要仅列出编写器的标识和状态，请键入：

```
list writers status
```

类似于以下内容的输出：

```
Listing writer status ...
* WRITER System Writer
        - Status: 5 (VSS_WS_WAITING_FOR_BACKUP_COMPLETE)
        - Writer Failure code: 0x00000000 (S_OK)
        - Writer ID: {e8132975-6f93-4464-a53e-1050253ae220}
        - Instance ID: {7e631031-c695-4229-9da1-a7de057e64cb}
* WRITER Shadow Copy Optimization Writer
        - Status: 1 (VSS_WS_STABLE)
        - Writer Failure code: 0x00000000 (S_OK)
        - Writer ID: {4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f}
        - Instance ID: {9e362607-9794-4dd4-a7cd-b3d5de0aad20}
* WRITER Registry Writer
        - Status: 1 (VSS_WS_STABLE)
        - Writer Failure code: 0x00000000 (S_OK)
        - Writer ID: {afbab4a2-367d-4d15-a586-71dbb18f8485}
        - Instance ID: {e87ba7e3-f8d8-42d8-b2ee-c76ae26b98e8}
8 writers listed.
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)