---
title: 附加 vdisk
description: 用于**附加 vdisk**的 Windows 命令主题，该主题附加（有时称为装载或表面）虚拟硬盘（VHD），以使其作为本地硬盘驱动器出现在主计算机上。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 882ab875-0c14-4eb3-98ef-fd0e8fa40d9c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a3a903ed231e34ac902ce10b5342f27e772ac89f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851260"
---
# <a name="attach-vdisk"></a>附加 vdisk

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

附加（有时称为装载或曲面）虚拟硬盘（VHD），以使其作为本地硬盘驱动器出现在主计算机上。 如果 VHD 在附加时已有磁盘分区和文件系统卷，则会为 VHD 中的卷分配一个驱动器号。

> [!NOTE]
> 此命令仅适用于 Windows 7 和 Windows Server 2008 R2。

## <a name="syntax"></a>语法

```
attach vdisk [readonly] { [sd=<SDDL>] | [usefilesd] } [noerr]
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| readonly | 将 VHD 附加为只读。 任何写入操作都将返回错误。 |
| `sd=<SDDL string>` | 设置 VHD 上的用户筛选器。 筛选器字符串的格式必须为安全描述符定义语言（SDDL）。 默认情况下，用户筛选器允许访问，就像在物理磁盘上。 SDDL 字符串可能比较复杂，但最简单的形式是，保护访问的安全描述符称为自由访问控制列表（DACL）。 它的格式为： `D:<dacl_flags><string_ace1><string_ace2>`... `<string_acen>`<p>常见的 DACL 标志包括：<p>-  **。** 允许访问<p>- **D**。拒绝访问<p>常见权限包括：<p>- **GA**。 所有访问<p>- **GR** 读取权限<p>- **GW**。 写入访问权限<p>常见用户帐户包括：<p>- **BA**。 内置管理员<p>- **AU**。 经过身份验证的用户数<p>- **CO**。 创建者所有者<p>- **WD**。 所有人<p>示例：<p>**D:P：（A;;GR;;;AU**为所有经过身份验证的用户提供读取访问权限。<p>**D:P：（A;;GA;;;WD**为每个人提供完全访问权限。 |
| usefilesd | 指定应在 VHD 上使用 .vhd 文件上的安全描述符。 如果未指定**Usefilesd**参数，则 VHD 将不具有明确的安全描述符，除非使用**Sd**参数指定它。 |
| noerr | 仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="remarks"></a>备注

- 必须选择并分离 VHD，此操作才能成功。 使用 "**选择 vdisk** " 命令选择 VHD 并将焦点移动到该 VHD。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

若要将所选 VHD 附加为只读，请键入：

```
attach vdisk readonly
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [compact vdisk](compact-vdisk.md)

- [详细信息 vdisk](detail-vdisk.md)

- [分离 vdisk](detach-vdisk.md)

- [展开 vdisk](expand-vdisk.md)

- [merge vdisk](merge-vdisk.md)

- [选择 vdisk](select-vdisk.md)

- [成员列表](list_1.md)
