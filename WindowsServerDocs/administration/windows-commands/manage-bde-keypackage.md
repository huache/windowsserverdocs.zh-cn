---
title: manage-bde ms-fve-keypackage
description: Manage-bde ms-fve-keypackage 命令的参考文章，可为驱动器生成密钥包。
ms.topic: reference
ms.assetid: c631ef10-2a2f-4541-8578-292f2d4e9e80
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c0a5e812b47990fce1544d36815ca47b89db7c48
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037675"
---
# <a name="manage-bde-keypackage"></a>manage-bde ms-fve-keypackage

为驱动器生成密钥包。 此密钥包可以与修复工具结合使用来修复损坏的驱动器。

## <a name="syntax"></a>语法

```
manage-bde -keypackage [<drive>] [-ID <keyprotectoryID>] [-path <pathtoexternalkeydirectory>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<drive>` | 表示驱动器号后跟一个冒号。 |
| -ID | 使用带有此 ID 值指定的标识符的密钥保护程序创建密钥包。 **提示：** 使用 **manage-bde –保护程序– get** 命令，以及要为其创建密钥包的驱动器号，以获取用作 ID 值的可用 guid 列表。 |
| -路径 | 指定用于保存创建的密钥包的位置。 |
| -computername | 指定 manage-bde.exe 将用于修改其他计算机上的 BitLocker 保护。 你还可以使用 **-cn** 作为此命令的缩写形式。 |
| `<name>` | 表示要修改 BitLocker 保护的计算机的名称。 接受的值包括计算机的 NetBIOS 名称和计算机的 IP 地址。 |
| -? 或 /? | 在命令提示符下显示 brief Help。 |
| -help 或-h | 在命令提示符下显示完整的帮助。 |

### <a name="examples"></a>示例

若要基于 GUID 标识的密钥保护程序为驱动器 C 创建密钥包，并将密钥包保存到 F:\Folder，请键入：

```
manage-bde -keypackage C: -id {84E151C1...7A62067A512} -path f:\Folder
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [manage-bde 命令](manage-bde.md)
