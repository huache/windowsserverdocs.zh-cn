---
title: cacls
description: 用于显示或修改指定文件上的随机访问控制列表（DACL）的 cacls 命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b5bdbaaa-4557-48b8-80df-e75ee0d2f27d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d827199ea319bd41511f9abadfde8c6e8949976e
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82726019"
---
# <a name="cacls"></a>cacls

>[!IMPORTANT]
> 此命令已弃用。 请改用[icacls](icacls.md) 。  

显示或修改指定文件上的随机访问控制列表（DACL）。  

## <a name="syntax"></a>语法

```  
cacls <filename> [/t] [/m] [/l] [/s[:sddl]] [/e] [/c] [/g user:<perm>] [/r user [...]] [/p user:<perm> [...]] [/d user [...]]  
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<filename>` | 必需。 显示指定文件的 Acl。 |
| /t  | 更改当前目录和所有子目录中指定文件的 Acl。 |
| /m | 更改装载到目录的卷的 Acl。 |
| /l | 适用于符号链接本身，而不是目标。 |
| /s： sddl | 将 Acl 替换为 SDDL 字符串中指定的 Acl。 此参数对于 **/e**、 **/g**、 **/r**、 **/p**或 **/d**参数无效。 |
| /e | 编辑 ACL 而不是替换它。 |
| /c | 拒绝访问错误后继续。 |
| `/g user:<perm>` | 授予指定的用户访问权限，包括权限的有效值：<ul><li>无（ **n** ）</li><li>**r** -读取</li><li>**w** -写入</li><li>**c** -更改（写入）</li><li>**f** -完全控制</li></ul> |
| /r user [...] | 吊销指定用户的访问权限。 仅当与 **/e**参数一起使用时才有效。 |
| `[/p user:<perm> [...]` | 替换指定用户的访问权限，包括权限的有效值：<ul><li>无（ **n** ）</li><li>**r** -读取</li><li>**w** -写入</li><li>**c** -更改（写入）</li><li>**f** -完全控制</li></ul> |
| [/d user [...] | 拒绝指定的用户访问。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="sample-output"></a>示例输出

| 输出 | 访问控制项（ACE）适用于 |
-------- | ------------------------------------- |
| OI | 对象继承。 此文件夹和文件。 |
| CI | 容器继承。 此文件夹和子文件夹。 |
| IO | 仅继承。 ACE 不适用于当前文件/目录。 |
| 无输出消息 | 仅限此文件夹。 |
| OICI | 此文件夹、子文件夹和文件。 |
| OICI排 | 仅子文件夹和文件。 |
| CI排 | 仅子文件夹。 |
| OI排 | 仅文件。 |

#### <a name="remarks"></a>备注

- 您可以使用通配符（**？** 和 **&#42;**）来指定多个文件。

- 可以指定多个用户。  

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [icacls](icacls.md)
