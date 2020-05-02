---
title: icacls
description: 用于显示或修改指定文件上的随机访问控制列表（DACL）的 icacls 命令的参考主题，并将存储的 Dacl 应用于指定目录中的文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 403edfcc-328a-479d-b641-80c290ccf73e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 08/21/2018
ms.openlocfilehash: dcf4fa9fa9205a762ead99ac4a8486ac04c23514
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724877"
---
# <a name="icacls"></a>icacls

显示或修改指定文件上的随机访问控制列表 (DACL)，并将存储的 DACL 应用于指定目录中的文件。

> [!NOTE]
> 此命令替换弃用的[cacls 命令](cacls.md)。

## <a name="syntax"></a>语法

```
icacls <filename> [/grant[:r] <sid>:<perm>[...]] [/deny <sid>:<perm>[...]] [/remove[:g|:d]] <sid>[...]] [/t] [/c] [/l] [/q] [/setintegritylevel <Level>:<policy>[...]]
icacls <directory> [/substitute <sidold> <sidnew> [...]] [/restore <aclfile> [/c] [/l] [/q]]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<filename>` | 指定要为其显示 Dacl 的文件。 |
| `<directory>` | 指定要为其显示 Dacl 的目录。 |
| /t  | 对当前目录及其子目录中的所有指定文件执行操作。 |
| /c | 即使存在任何文件错误，也会继续操作。 仍会显示错误消息。 |
| /l | 对符号链接而不是其目标执行操作。 |
| /q | 禁止显示成功消息。 |
| [/save `<ACLfile>` [/t] [/c] [/l] [/q]] | 将所有匹配文件的 Dacl 存储到*ACLfile*中，以便以后用于 **/restore**。 |
| [/setowner `<username>` [/t] [/c] [/l] [/q]] | 将所有匹配文件的所有者更改为指定用户。 |
| [/findsid `<sid>` [/t] [/c] [/l] [/q]] | 查找所有匹配文件，其中包含显式提及指定安全标识符（SID）的 DACL。 |
| [/verify [/t] [/c] [/l] [/q]] | 查找其 Acl 不规范或长度与 ACE （访问控制项）计数不一致的所有文件。 |
| [/reset [/t] [/c] [/l] [/q]] | 将 Acl 替换为所有匹配文件的默认继承 Acl。 |
| [/grant [： r] \<sid>：<perm>[...]] | 授予指定的用户访问权限。 权限替换之前授予的显式权限。<p>不添加 **： r**，这意味着将权限添加到以前授予的任何显式权限。 |
| [/deny \<sid>：<perm>[...]] | 显式拒绝指定的用户访问权限。 将为所述权限添加显式拒绝 ACE，并删除任何显式授权中的相同权限。 |
| [/remove`[:g | :d]]` `<sid>`[...]/t/c/l/q | 从 DACL 中移除指定 SID 的所有匹配项。 此命令还可以使用：<ul><li>**： g** -删除已授予的对指定 SID 的所有权限。</li><li>**:d** -删除对指定 SID 的所有拒绝的权限。 |
| [/setintegritylevel [（CI）（OI）] `<Level>:<Policy>`[...]] | 将完整性 ACE 显式添加到所有匹配的文件。 可将级别指定为：<ul><li>**l** -低</li><li>**m**-中型</li><li>**h** -高</li></ul>完整性 ACE 的继承选项可能在级别之前，只适用于目录。 |
| [/substitute `<sidold> <sidnew>` [...]] | 使用新的 SID （*sidnew*）替换现有 sid （*sidold*）。 要求将`<directory>`与参数一起使用。 |
| /restore `<ACLfile>` [/c] [/l] [/q] | 将存储的 Dacl `<ACLfile>`从应用到指定目录中的文件。 要求将`<directory>`与参数一起使用。 |
| /inheritancelevel:`[e | d | r]` | 设置继承级别，可以是：<ul><li>**e** -启用继承</li><li>**d** -禁用继承并复制 ace</li><li>**r** -删除所有继承的 ace</li></ul> |

## <a name="remarks"></a>备注

- Sid 可以是数字或友好名称格式。 如果使用数字形式，请将通配符 **&#42;** 到 SID 的开头。

- 此命令保留 ACE 条目的规范顺序，如下所示：  

    - 显式拒绝

    -  显式授予

    - 继承的拒绝

    - 继承的授权

- `<perm>`选项是可通过以下形式之一指定的权限掩码：

    - 一系列简单权限：

      - **F** -完全访问权限

      - **M**-修改访问权限

      - **RX** -读取和执行访问

      - **R** -只读访问

      - **W** -只写访问

    - 以逗号分隔的特定权限的列表（以逗号分隔）：

      - **D** -Delete

      - **RC** -读取控制

      - **WDAC** -写入 DAC

      - **WO**写入所有者

      - **S** -同步

      - **AS**访问系统安全

      - **MA** -允许的最大值

      - **GR** -通用读取

      - **GW** -泛型写入

      - **GE** -泛型执行

      - **GA** -一般全部

      - **RD** -读取数据/列表目录

      - **WD** -写入数据/添加文件

      - **AD** -追加数据/添加子目录

      - **REA** -读取扩展属性

      - **WEA** -写入扩展属性

      - **X** -执行/遍历

      - **DC** -删除子项

      - **RA** -读取属性

      - **WA** -写入属性

  - 继承权限可能在任一`<perm>`形式之前，只适用于目录：

      - **（OI）** -对象继承

      - **（CI）** -容器继承

      - **（IO）** -仅继承

      - **（NP）** -不传播继承

## <a name="examples"></a>示例

若要将 C：\Windows 目录及其子目录中所有文件的 Dacl 保存到 ACLFile 文件，请键入：

```
icacls c:\windows\* /save aclfile /t
```

要还原 ACLFile 中存在的每个文件的 Dacl 及其子目录，请键入：

```
icacls c:\windows\ /restore aclfile
```

若要授予用户 User1 删除和写入名为 Test1 的文件的 DAC 权限，请键入：

```
icacls test1 /grant User1:(d,wdac)
```

若要向用户授予 SID S-1-1-0 删除和写入 DAC 权限的用户，请在名为 Test2 的文件中键入：

```
icacls test2 /grant *S-1-1-0:(d,wdac)
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
