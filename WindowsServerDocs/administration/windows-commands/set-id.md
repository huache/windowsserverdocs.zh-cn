---
title: 设置 ID
description: 有关 Diskpart 集 ID 的参考文章，请参阅为具有焦点的分区更改分区类型字段。
ms.topic: reference
ms.assetid: 5793d7ad-827e-4285-b2c6-ae60eeb0e886
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e3b9ce5b885ca9c8277842b16c816274fff0ead8
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024951"
---
# <a name="set-id"></a>设置 ID

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

Diskpart Set ID 命令将更改具有焦点的分区的 "分区类型" 字段。

> [!IMPORTANT]
> 此命令仅供原始设备制造商 \( oem 使用 \) 。 更改具有此参数的分区类型字段可能导致计算机出现故障或无法启动。 除非你是使用 gpt 磁盘的 OEM 或经验丰富的磁盘，否则不应使用此参数更改 gpt 磁盘上的分区类型字段。 相反，请始终使用 [create partition efi](create-partition-efi.md) 命令创建 efi 系统分区，使用 [create partition Msr](create-partition-msr.md) 命令创建 Microsoft 保留分区，并使用 [create partition PRIMARY](create-partition-primary.md) 命令而不使用 ID 参数在 gpt 磁盘上创建主分区。



## <a name="syntax"></a>语法

```
set id={ <byte> | <GUID> } [override] [noerr]
```

### <a name="parameters"></a>参数

| 参数 |                                                                                                                                                                                                                                                                                                                                                                   说明                                                                                                                                                                                                                                                                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <byte>   |                                                                                                                                                                                                       对于主启动记录 \( MBR \) 磁盘，以十六进制格式为分区指定 "类型" 字段的新值。 除了指定 LDM 分区的类型0x42 以外，可以使用此参数指定任何分区类型字节。 请注意，在指定十六进制分区类型时，将省略前导0x。                                                                                                                                                                                                       |
|  <GUID>   | 对于 GUID 分区表 \( gpt \) 磁盘，为分区的类型字段指定新的 GUID 值。 可识别的 Guid 包括：<p>-EFI 系统分区： c12a7328 \- f81f \- 11d2 \- ba4b \- 00a0c93ec93b<br />-基本数据分区： ebd0a0a2 \- b9e5 \- 4433 \- 87c0 \- 68b6b72699c7<p>任何分区类型 GUID 都可与此参数一起指定，如下所示：<p>-Microsoft 保留分区： e3c9e316 \- 0b5c \- 4db8 \- 817d \- f92df00215ae<br />-动态磁盘上的 LDM 元数据分区： 5808c8aa \- 7e8f \- 42e0 \- 85d2 \- e1e90434cfb3<br />-动态磁盘上的 LDM 数据分区： af9b60a0 \- 1431 \- 4f62 \- bc68 \- 3311714a69ad<br />-Cluster metadata partition： db97dba9 \- 0840 \- 4bae \- 97f0 \- ffb9a327c7e1 |
| override  |                                                                强制在更改分区类型前卸除卷上的文件系统。 当你运行 " **设置 id** " 命令时，DiskPart 尝试锁定并卸除卷上的文件系统。 如果未指定 **override** ，并且对锁定文件系统的调用失败， \( 例如，由于存在一个打开的句柄 \) ，则操作将失败。 指定 **替代** 后，即使对锁定文件系统的调用失败，也会强制卸载，并且卷的任何打开的句柄都将变为无效。<p>此命令仅适用于 Windows 7 和 Windows Server 2008 R2。                                                                 |
|   noerr   |                                                                                                                                                                                                                                                                    仅用于脚本编写。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。                                                                                                                                                                                                                                                                    |

## <a name="remarks"></a>注解

-   除了前面提到的限制之外，DiskPart 不会检查你指定的值的有效性， \( 但请确保它是十六进制格式的字节或 GUID \) 。

-   此命令不适用于动态磁盘或 Microsoft 保留分区。

## <a name="examples"></a>示例
若要将 "类型" 字段设置为0x07 并强制卸除文件系统，请键入：

```
set id=0x07 override
```

若要将 "类型" 字段设置为基本数据分区，请键入：

```
set id=ebd0a0a2-b9e5-4433-87c0-68b6b72699c7
```

## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)




