---
title: convert basic
description: 用于转换基本命令的参考文章，可将空的动态磁盘转换为基本磁盘。
ms.topic: article
ms.assetid: 61329896-3b56-4959-8d58-45cbe18ba860
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 88ad686cd47bc9c347469697511a81f6cf4ae835
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87892595"
---
# <a name="convert-basic"></a>convert basic

将空的动态磁盘转换为基本磁盘。 若要成功执行此操作，必须选择一个动态磁盘。 使用 "[选择磁盘" 命令](select-disk.md)选择动态磁盘并将焦点移动到该磁盘。

> [!IMPORTANT]
> 若要将磁盘转换成基本磁盘，该磁盘必须为空。 转换磁盘之前，请备份数据，然后删除全部分区或卷。

> [!NOTE]
> 有关如何使用此命令的说明，请参阅[将动态磁盘改回为基本磁盘](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755238(v=ws.11))) 。

## <a name="syntax"></a>语法

```
convert basic [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要将所选的动态磁盘转换为基本磁盘，请键入：

```
convert basic
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [转换命令](convert.md)
