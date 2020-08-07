---
title: showmount
description: 用于显示已装载目录的 showmount 的参考文章。
ms.topic: article
ms.assetid: a6dd562e-e3bd-4ee6-be3b-6d29e29fd20e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0be623eadd56a55a87f2df57fec9b4c6558770c9
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87882402"
---
# <a name="showmount"></a>showmount

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

可以使用**showmount**显示已装载的目录。

## <a name="syntax"></a>语法
```
showmount {-e|-a|-d} <Server>
```

## <a name="description"></a>说明
**Showmount**命令 \- 行实用工具显示*服务器*指定的计算机上的 NFS 服务器导出的已装载文件系统的相关信息。 如果未提供*服务器*， **showmount**将显示运行**showmount**命令的计算机的相关信息。

您必须提供以下选项之一：

- ** \- e** -显示服务器上导出的所有文件系统。
- ** \- a** -显示所有网络文件系统 \( NFS \) 客户端和服务器上每个已装载的目录。
- ** \- d** -显示 NFS 客户端当前装载的服务器上的所有目录。

## <a name="see-also"></a>另请参阅
[网络文件系统命令参考服务](services-for-network-file-system-command-reference.md)