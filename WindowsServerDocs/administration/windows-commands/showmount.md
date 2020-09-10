---
title: showmount
description: 用于显示已装载目录的 showmount 的参考文章。
ms.topic: reference
ms.assetid: a6dd562e-e3bd-4ee6-be3b-6d29e29fd20e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e0a03c7e08c80e4cf0b99bbcb74aeff1deccdb1e
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640956"
---
# <a name="showmount"></a>showmount

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

可以使用 **showmount** 显示已装载的目录。

## <a name="syntax"></a>语法
```
showmount {-e|-a|-d} <Server>
```

## <a name="description"></a>说明
**Showmount**命令 \- 行实用工具显示*服务器*指定的计算机上的 NFS 服务器导出的已装载文件系统的相关信息。 如果未提供 *服务器* ， **showmount** 将显示运行 **showmount** 命令的计算机的相关信息。

您必须提供以下选项之一：

- ** \- e** -显示服务器上导出的所有文件系统。
- ** \- a** -显示所有网络文件系统 \( NFS \) 客户端和服务器上每个已装载的目录。
- ** \- d** -显示 NFS 客户端当前装载的服务器上的所有目录。

## <a name="see-also"></a>另请参阅
[网络文件系统命令参考服务](services-for-network-file-system-command-reference.md)