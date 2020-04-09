---
title: bitsadmin addfilewithranges
description: 适用于**bitsadmin addfilewithranges**的 Windows 命令主题，用于将文件添加到指定的作业。 BITS 从远程文件下载指定的范围。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: df0ce0bf-dff1-4a48-a16f-fd2f4d5f7189
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 60b448550473691bbbaf573f99f00609e14e0f42
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850950"
---
# <a name="bitsadmin-addfilewithranges"></a>bitsadmin addfilewithranges

将文件添加到指定的作业。 BITS 从远程文件下载指定的范围。 此开关仅对下载作业有效。

## <a name="syntax"></a>语法

```
bitsadmin /AddFileWithRanges <Job> <RemoteURL> <LocalName> <RangeList>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| RemoteURL | 服务器上的文件的 URL。 |
| LocalName | 本地计算机上的文件的名称。 必须包含文件的绝对路径。 |
| RangeList | 偏移量：长度对的逗号分隔列表。 使用冒号将 offset 值与 length 值分隔开。 例如，如果值为 `0:100,2000:100,5000:eof`，则会告诉 BITS 传输100个字节，偏移量为0，100字节从偏移为2000，剩余字节从偏移量5000传输到文件末尾。 |

## <a name="remarks"></a>备注

- 标记**eof**是 *\<RangeList >* 的偏移量和长度对中的有效长度值。 它指示服务读取到指定文件的末尾。

- 如果同时指定了长度为零的范围和具有相同偏移量的另一个范围，AddFileWithRanges 将失败并出现错误代码0x8020002c，如：

    `C:\bits>bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:0,100:5`

    **错误消息：** 无法将文件添加到作业-0x8020002c。 字节范围的列表包含一些不受支持的重叠范围。

    **解决方法：** 不要首先指定长度为零的范围。 例如，使用： 

    `bitsadmin /addfilewithranges j2 http://bitsdc/dload/1k.zip c:\1k.zip 100:5,100:0.`

## <a name="examples"></a>示例

下面的示例告知 BITS 要将100字节从偏移量为0、100字节从偏移为2000、从偏移量5000传输到文件末尾。

```
C:\>bitsadmin /addfilewithranges http://downloadsrv/10mb.zip c:\10mb.zip 0:100,2000:100,5000:eof
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)