---
title: jetpack
description: Jetpack 命令的参考主题，用于压缩 Windows Internet 名称服务（WINS）或动态主机配置协议（DHCP）数据库。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 82a2b7ef-0db5-4575-a028-8acb0bf6c7ba
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6d77f9c964f5820fc7a44b803bb765e94cb35637
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83818247"
---
# <a name="jetpack"></a>jetpack

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

压缩 Windows Internet 名称服务（WINS）或动态主机配置协议（DHCP）数据库。 建议在 WINS 数据库接近 30 MB 时将其压缩。

Jetpack 通过以下方式压缩数据库：

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
| `<temp_database_name>` | 指定 jetpack 创建的临时数据库文件的名称。<p>注意：压缩过程完成后，将删除此临时文件。 若要使此命令正常工作，必须确保临时文件名是唯一的，并且具有该名称的文件不存在。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要压缩 WINS 数据库（其中**Tmp**是临时数据库，而**wins-a**是 wins 数据库），请键入：

```
cd %SYSTEMROOT%\SYSTEM32\WINS
NET STOP WINS
jetpack Wins.mdb Tmp.mdb
NET start WINS
```

若要压缩 DHCP 数据库，其中**Tmp**是临时数据库，而**dhcp**是 dhcp 数据库，请键入：

```
cd %SYSTEMROOT%\SYSTEM32\DHCP
NET STOP DHCPSERVER
jetpack Dhcp.mdb Tmp.mdb
NET start DHCPSERVER
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
