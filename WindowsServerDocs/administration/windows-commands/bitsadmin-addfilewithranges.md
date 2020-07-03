---
title: bitsadmin addfilewithranges
description: Bitsadmin addfilewithranges 命令的参考文章，可将文件添加到指定的作业。 BITS 从远程文件下载指定的范围。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: df0ce0bf-dff1-4a48-a16f-fd2f4d5f7189
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5439cfb8330cda7c51150c720fe45faccca8e1ec
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927079"
---
# <a name="bitsadmin-addfilewithranges"></a>bitsadmin addfilewithranges

将文件添加到指定的作业。 BITS 从远程文件下载指定的范围。 此开关仅对下载作业有效。

## <a name="syntax"></a>语法

```
bitsadmin /addfilewithranges <job> <remoteURL> <localname> <rangelist>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| remoteURL | 服务器上的文件的 URL。 |
| localname | 本地计算机上的文件的名称。 必须包含文件的绝对路径。 |
| rangelist | 偏移量：长度对的逗号分隔列表。 使用冒号将 offset 值与 length 值分隔开。 例如，如果值为，则 "通知位" 将从偏移量 `0:100,2000:100,5000:eof` 0 传输100个字节，从偏移为 2000 100 个字节，将其余字节从偏移量5000传输到文件末尾。 |

## <a name="remarks"></a>备注

- 标记**eof**是中的偏移量和长度对内的有效长度值 `<rangelist>` 。 它指示服务读取到指定文件的末尾。

- `addfilewithranges`如果使用相同的偏移量指定了长度为零的范围以及另一个范围，则该命令将失败并出现错误代码0x8020002c，例如：

    `c:\bits>bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:0,100:5`

    **错误消息：** 无法将文件添加到作业-0x8020002c。 字节范围的列表包含一些不受支持的重叠范围。

    **解决方法：** 不要首先指定长度为零的范围。 例如，使用 `bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:5,100:0`

## <a name="examples"></a>示例

如果为，则从偏移量为0传输100个字节，从偏移量2000传输100个字节，并将剩余字节从偏移量5000传输到文件的末尾：

```
bitsadmin /addfilewithranges http://downloadsrv/10mb.zip c:\10mb.zip 0:100,2000:100,5000:eof
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
