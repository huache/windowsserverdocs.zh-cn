---
title: showmount
description: 用于显示已装载目录的 showmount 的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a6dd562e-e3bd-4ee6-be3b-6d29e29fd20e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6fa61d47bb14cf21d93beec0a6e9257b9f66737b
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80834220"
---
# <a name="showmount"></a>showmount

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

可以使用**showmount**显示已装载的目录。  
  
## <a name="syntax"></a>语法  
```
showmount {-e|-a|-d} <Server>  
```

## <a name="description"></a>说明  
**Showmount**命令\-line 实用工具显示*服务器*指定的计算机上的 NFS 服务器导出的已装载文件系统的相关信息。 如果未提供*服务器*， **showmount**将显示运行**showmount**命令的计算机的相关信息。  
  
您必须提供以下选项之一：  
  
- **\-e** -显示服务器上导出的所有文件系统。  
- **\-** -显示所有网络文件系统 \(NFS\) 客户端和服务器上安装的每个目录。  
- **\-d** -显示 NFS 客户端当前装载的服务器上的所有目录。  
  
## <a name="see-also"></a>另请参阅  
[网络文件系统命令参考服务](services-for-network-file-system-command-reference.md)  