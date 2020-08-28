---
title: label
description: "\"标签\" 命令的参考文章，其中创建、更改或删除卷标 (即磁盘的名称) 。"
ms.topic: reference
ms.assetid: bbae8bdd-97d4-4566-9118-7c95aa07645f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 486461059e90d0d1e1c6fa413e6db595f82924bb
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028195"
---
# <a name="label"></a>label

创建、更改或删除卷标 (即磁盘的名称) 。 如果在没有参数的情况下使用，则 " **标签** " 命令将更改当前卷标签或删除现有标签。

## <a name="syntax"></a>语法

```
label [/mp] [<volume>] [<label>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /mp | 指定应将卷视为装入点或卷名。 |
| `<volume>` | 指定驱动器号 (后跟冒号) 、装入点或卷名。 如果指定了卷名称，则不需要 **/mp** 参数。 |
| `<label>` | 指定卷的标签。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="remarks"></a>注解

- Windows 将显示卷标和序列号 (如果它有一个) 作为目录列表的一部分。

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

3. 按 **Y** 可删除当前标签，如果要保留现有标签，则为 **N** 。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)