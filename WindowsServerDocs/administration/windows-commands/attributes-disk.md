---
title: 属性磁盘
description: 用于显示、设置或清除磁盘属性的 "**属性磁盘**" 的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: eed57071-c1c6-4394-9542-62b52a878c92
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f3c29a009a1efdfb7fed3d04d194cc8cfd2ea4eb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851240"
---
# <a name="attributes-disk"></a>属性磁盘

显示、设置或清除磁盘的属性。

## <a name="syntax"></a>语法

```
attributes disk [{set | clear}] [readonly] [noerr]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| set | 设置具有焦点的磁盘的指定属性。 |
| 清除 | 清除具有焦点的磁盘的指定属性。 |
| readonly | 指定磁盘为只读。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="remarks"></a>备注

-   当**属性 "磁盘**" 用于显示磁盘的当前属性时，"启动磁盘" 属性表示用于启动计算机的磁盘。 对于动态镜像，将为包含启动卷的启动丛的磁盘显示。

-   必须选择磁盘，"属性"**磁盘**命令才能成功。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要查看所选磁盘的属性，请键入：

```
attributes disk
```

若要将所选磁盘设置为只读，请键入：

```
attributes disk set readonly
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)