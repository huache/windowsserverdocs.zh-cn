---
title: '中断 (卷影副本卷) '
description: 用于中断命令的参考文章，此命令将卷影副本卷与 VSS 解除阻止，并使其作为常规卷进行访问。
ms.topic: article
ms.assetid: de2b6c95-1c2e-4a43-bec5-341a9014371b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 125f986152d10844bbab5a7b57a1a2ea4080aa3e
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880460"
---
# <a name="break-shadow-copy-volume"></a>中断 (卷影副本卷) 

将卷影副本卷与 VSS 解除映射，并使其作为常规卷进行访问。 然后，可以使用驱动器号 (如果分配的) 或卷名。 如果不使用参数， **break**将在命令提示符下显示帮助。

> [!NOTE]
> 此命令仅适用于导入后的硬件卷影副本。
>
> 公开的卷（例如它们源自的卷影副本）默认为只读。 对卷的访问直接对硬件提供程序进行，而不记录卷的卷影副本。

## <a name="syntax"></a>语法

```
break [writable] <setid>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 编写 | 启用对卷的读/写访问。 |
| \<setid> | 指定卷影副本集的 ID。 可以在*SetID*参数中使用卷影副本 ID 的别名，该 ID 由**load metadata**命令存储为环境变量。 |

## <a name="examples"></a>示例

要使用别名创建卷影副本，可在操作系统中将其作为可写卷 Alias1：

```
break writable %Alias1%
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)