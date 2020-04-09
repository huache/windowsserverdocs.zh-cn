---
title: detail disk
description: Windows 命令主题，其中显示了详细信息磁盘，其中显示了所选磁盘的属性以及该磁盘上的卷。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6b09cf40-8d93-452b-b449-5242e62a4102
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0d0768d45c0f56ba549ff54064c4e74ae3048e41
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846450"
---
# <a name="detail-disk"></a>detail disk

显示选中磁盘的属性和该磁盘上的卷。

## <a name="syntax"></a>语法

```
detail disk
```

## <a name="remarks"></a>备注

-   若要成功执行此操作，必须选择磁盘。 使用 "**选择磁盘**" 命令选择磁盘，并将焦点移动到该磁盘。
-   如果所选磁盘是虚拟硬盘（VHD），**详细信息磁盘**会将磁盘的总线类型报告为 "虚拟"。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要查看所选磁盘的属性以及磁盘中的卷的相关信息，请键入：
```
detail disk
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

