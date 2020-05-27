---
title: 标签
description: "\"标签\" 命令的参考主题，用于创建、更改或删除磁盘的卷标（即名称）。"
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bbae8bdd-97d4-4566-9118-7c95aa07645f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f2d09328f79215c497bcb0ea4549b1f6ac227994
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83817257"
---
# <a name="label"></a>标签

创建、更改或删除磁盘的卷标（即名称）。 如果在没有参数的情况下使用，则 "**标签**" 命令将更改当前卷标签或删除现有标签。

## <a name="syntax"></a>语法

```
label [/mp] [<volume>] [<label>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /mp | 指定应将卷视为装入点或卷名。 |
| `<volume>` | 指定驱动器号（后跟冒号）、装入点或卷名。 如果指定了卷名称，则不需要 **/mp**参数。 |
| `<label>` | 指定卷的标签。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="remarks"></a>备注

- Windows 在目录列表中显示卷标和序列号（如果有的话）。

- NTFS 卷标长度最多可包含32个字符，包括空格。 NTFS 卷标签保留并显示创建标签时使用的大小写。

## <a name="examples"></a>示例

若要在驱动器 A 中为包含7月销售信息的磁盘添加标签，请键入：

```
label a:sales-july
```

若要查看和删除驱动器 C 的当前标签，请执行以下步骤：

1. 在命令提示符处，键入：

   ```
   label
   ```

   应显示类似于以下内容的输出：

   ```
   Volume in drive C: is Main Disk
   Volume Serial Number is 6789-ABCD
   Volume label (32 characters, ENTER for none)?
   ```

2. 按 Enter。 应显示以下提示：

   ```
   Delete current volume label (Y/N)?
   ```

3. 按**Y**可删除当前标签，如果要保留现有标签，则为**N** 。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)