---
title: ftp type
description: Ftp 类型命令的参考文章，用于设置或显示文件传输类型。
ms.topic: reference
ms.assetid: 6e96dcd4-08f8-4e7b-90b7-1e1761fea4c7
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 943ac3ca85c1e99118ea772338ea427d758927cb
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639394"
---
# <a name="ftp-type"></a>ftp type

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

设置或显示文件传输类型。 **Ftp**命令支持 ASCII (默认) 和二进制图像文件传输类型：

- 建议在传输文本文件时使用 ASCII。 在 ASCII 模式下，执行与网络标准字符集之间的字符转换。 例如，根据目标操作系统，将根据需要转换行尾字符。

- 建议在传输可执行文件时使用二进制。 在二进制模式下，文件以单字节单位传输。

## <a name="syntax"></a>语法

```
type [<typename>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `[<typename>]` | 指定文件传输类型。 如果未指定此参数，则显示当前类型。|

### <a name="examples"></a>示例

若要将文件传输类型设置为 ASCII，请键入：

```
type ascii
```

若要将 "传输文件类型" 设置为 "二进制"，请键入：

```
type binary
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
