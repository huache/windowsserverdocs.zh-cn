---
title: detail disk
description: 详细信息磁盘的参考主题，其中显示了所选磁盘的属性以及该磁盘上的卷。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6b09cf40-8d93-452b-b449-5242e62a4102
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a746506d6c9609e3214dbd48e5fa91f52d16ab4d
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82710519"
---
# <a name="detail-disk"></a>detail disk

显示所选磁盘的属性和该磁盘上的卷。

## <a name="syntax"></a>语法

```
detail disk
```

## <a name="remarks"></a>备注

-   若要成功执行此操作，必须选择磁盘。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。
-   如果所选磁盘是虚拟硬盘（VHD），**详细信息磁盘**会将磁盘的总线类型报告为 "虚拟"。

## <a name="examples"></a>示例

若要查看所选磁盘的属性以及磁盘中的卷的相关信息，请键入：
```
detail disk
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

