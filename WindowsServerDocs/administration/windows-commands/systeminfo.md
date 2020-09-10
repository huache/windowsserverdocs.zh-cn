---
title: systeminfo
description: Systeminfo.exe 参考文章，其中显示了有关计算机及其操作系统的详细配置信息，包括操作系统配置、安全信息、产品 ID 和硬件属性， (如 RAM、磁盘空间和网卡) 。
ms.topic: reference
ms.assetid: 39954968-3c2e-4d3e-9d89-c9c43347461e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b8db86467c6d3190edd6c041951bf3c30eb21cc4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626743"
---
# <a name="systeminfo"></a>systeminfo

显示有关计算机及其操作系统的详细配置信息，包括操作系统配置、安全信息、产品 ID 和硬件属性 (如 RAM、磁盘空间和网卡) 。



## <a name="syntax"></a>语法

```
Systeminfo [/s <Computer> [/u <Domain>\<UserName> [/p <Password>]]] [/fo {TABLE | LIST | CSV}] [/nh]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/s \<Computer>|指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。|
|/u \<Domain>\<UserName>|用指定用户帐户的帐户权限运行命令。 如果未指定 **/u** ，则此命令将使用当前登录到发出命令的计算机的用户的权限。|
|/p \<Password>|指定在 **/u** 参数中指定的用户帐户的密码。|
|/fo \<Format>|用以下值之一指定输出格式：</br>TABLE：在表中显示输出。</br>LIST：在列表中显示输出。</br>CSV：以逗号分隔值格式显示输出。|
|/nh|取消输出中的列标题。 当 **/fo** 参数设置为表或 CSV 时有效。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a>示例

若要查看名为 Srvmain 的计算机的配置信息，请键入：

**systeminfo.exe/s srvmain**

若要远程查看位于 Maindom 域上名为 Srvmain2 的计算机的配置信息，请键入：

**systeminfo.exe/s srvmain2/u maindom\hiropln**

若要远程查看位于 Maindom 域上名为 Srvmain2 的计算机的 (列表格式的配置信息) ，请键入：

**systeminfo.exe/s srvmain2/u maindom\hiropln/p p@ssW23 /fo list**

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)