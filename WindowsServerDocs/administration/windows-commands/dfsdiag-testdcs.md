---
title: dfsdiag TestDCs
description: 适用于 dfsdiag TestDCs 的 Windows 命令主题，用于检查指定域中的域控制器的配置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: abb915ab-23eb-45d7-9a2e-b6b9a5756a70
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 092ce3710eb6d209f596683bd4ad054dadd11aa3
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80846311"
---
# <a name="dfsdiag-testdcs"></a>dfsdiag TestDCs

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

通过在指定域中的每个域控制器上执行以下测试来检查域控制器的配置：  
  
-   验证分布式文件系统（DFS）命名空间服务是否正在运行，并且其启动类型是否设置为 "自动"。  
  
-   检查 NETLOGON 和 SYSvol 是否支持站点开销的引用。  
  
-   验证站点关联的一致性（按主机名和 IP 地址）。

## <a name="syntax"></a>语法  
  
```  
dfsdiag /TestDCs [/Domain:<Domain name>]  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|说明|  
|-------|--------|  
|/Domain：`<domain_name>`|要检查的域。|  
  
## <a name="remarks"></a>备注  

/Domain 是一个可选参数。 默认值为本地主机联接到的本地域。  
  
## <a name="examples"></a><a name=BKMK_Examples></a>示例  
若要验证 Contoso.com 域中的域控制器的配置，请键入：  
  
```  
dfsdiag /TestDCs /Domain:Contoso.com  
```  
  
## <a name="additional-references"></a>其他参考  
  
-   - [命令行语法项](command-line-syntax-key.md)  
  
-   [dfsdiag](dfsdiag.md)  
  

