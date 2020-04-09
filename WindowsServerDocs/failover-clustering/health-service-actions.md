---
title: 运行状况服务操作
ms.prod: windows-server
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
author: cosmosdarwin
ms.date: 08/14/2017
ms.openlocfilehash: a4ef08a4ca552211b64d11677153775d6b18b4fa
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80827620"
---
# <a name="health-service-actions"></a>运行状况服务操作

> 适用于： Windows Server 2019、Windows Server 2016

运行状况服务是 Windows Server 2016 中的一项新功能，可改进运行存储空间直通的群集的日常监视和操作体验。

## <a name="actions"></a>Actions  

下一部分介绍运行状况服务自动化的工作流。 要验证确实正在自主执行一项操作，或者要跟踪其进度或结果，运行状况服务会生成“操作”。 与日志不同，完成后不久操作会消失，并且主要用于深入了解正在进行的活动，这些活动可能会影响性能或容量（例如还原复原或重新平衡数据）。  

### <a name="usage"></a>用法  

一个新的 PowerShell cmdlet 会显示所有操作：  

```PowerShell
Get-StorageHealthAction  
```

### <a name="coverage"></a>涵盖范围广  

在 Windows Server 2016 中， **StorageHealthAction** cmdlet 可以返回以下任何信息：  

-   停用失败、断开连接或未响应的物理磁盘  

-   切换存储池以使用替代物理磁盘  

-   还原数据的完全复原能力  

-   重新平衡存储池  

## <a name="see-also"></a>另请参阅

- [Windows Server 2016 中的运行状况服务](health-service-overview.md)
- [MSDN 上的开发人员文档、示例代码和 API 参考](https://msdn.microsoft.com/windowshealthservice)
