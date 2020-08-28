---
title: jetpack
description: Jetpack 命令的参考文章，该命令将 Windows Internet 名称服务 (WINS) 或动态主机配置协议 (DHCP) 数据库中压缩。
ms.topic: reference
ms.assetid: 82a2b7ef-0db5-4575-a028-8acb0bf6c7ba
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bf2664c142a169982acc0d11c34a53aea193d030
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89035415"
---
# <a name="jetpack"></a>jetpack

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将 Windows Internet 名称服务 (WINS) 或动态主机配置协议 (DHCP) 数据库压缩。 建议在 WINS 数据库接近 30 MB 时将其压缩。

Jetpack.exe 通过以下方法压缩数据库：

1. 将数据库信息复制到临时数据库文件。

2. 删除原始数据库文件，无论是 WINS 还是 DHCP。

3. 将临时数据库文件重命名为原始文件名。

## <a name="syntax"></a>语法

```
jetpack.exe <database_name> <temp_database_name>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| `<database_name>` | 指定原始数据库文件的名称。 |
| `<temp_database_name>` | 指定 jetpack.exe 创建的临时数据库文件的名称。<p>注意：压缩过程完成后，将删除此临时文件。 若要使此命令正常工作，必须确保临时文件名是唯一的，并且具有该名称的文件不存在。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要压缩 WINS 数据库（其中 **Tmp** 是临时数据库，而 **wins-a** 是 wins 数据库），请键入：

```
cd %SYSTEMROOT%\SYSTEM32\WINS
NET STOP WINS
jetpack Wins.mdb Tmp.mdb
NET start WINS
```

若要压缩 DHCP 数据库，其中 **Tmp** 是临时数据库，而 **dhcp** 是 dhcp 数据库，请键入：

```
cd %SYSTEMROOT%\SYSTEM32\DHCP
NET STOP DHCPSERVER
jetpack Dhcp.mdb Tmp.mdb
NET start DHCPSERVER
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
