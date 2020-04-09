---
title: systeminfo
description: 适用于 systeminfo.exe 的 Windows 命令主题，其中显示有关计算机及其操作系统的详细配置信息，包括操作系统配置、安全信息、产品 ID 和硬件属性（如 RAM、磁盘空间和网卡）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 39954968-3c2e-4d3e-9d89-c9c43347461e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 41c2a499bc10f5b44f250958471b90f4b88dfede
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833570"
---
# <a name="systeminfo"></a>systeminfo

显示有关计算机及其操作系统的详细配置信息，包括操作系统配置、安全信息、产品 ID 和硬件属性（如 RAM、磁盘空间和网卡）。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
Systeminfo [/s <Computer> [/u <Domain>\<UserName> [/p <Password>]]] [/fo {TABLE | LIST | CSV}] [/nh]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/s \<计算机 >|指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。|
|/u \<域 >\<用户名 >|用指定用户帐户的帐户权限运行命令。 如果未指定 **/u** ，则此命令将使用当前登录到发出命令的计算机的用户的权限。|
|/p \<密码 >|指定在 **/u**参数中指定的用户帐户的密码。|
|/fo \<格式 >|用以下值之一指定输出格式：</br>TABLE：在表中显示输出。</br>LIST：在列表中显示输出。</br>CSV：以逗号分隔值格式显示输出。|
|/nh|取消输出中的列标题。 当 **/fo**参数设置为表或 CSV 时有效。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要查看名为 Srvmain 的计算机的配置信息，请键入：

**systeminfo.exe/s srvmain**

若要远程查看位于 Maindom 域上名为 Srvmain2 的计算机的配置信息，请键入：

**systeminfo.exe/s srvmain2/u maindom\hiropln**

若要远程查看位于 Maindom 域上名为 Srvmain2 的计算机的配置信息（列表格式），请键入：

**systeminfo.exe/s srvmain2/u maindom\hiropln/p p@ssW23/fo list**

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)