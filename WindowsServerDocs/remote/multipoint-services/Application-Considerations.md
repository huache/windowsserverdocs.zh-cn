---
title: 应用程序注意事项
description: MultiPoint 服务上应用的兼容性信息
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 445e6184-4e1e-4f10-ad3c-042f2a6c2f5f
author: evaseydl
manager: scottman
ms.author: evas
ms.date: 08/04/2016
ms.openlocfilehash: 04449db18febdb2e37ac5ef7f5eee4dfc02ba94d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859360"
---
# <a name="application-considerations"></a>应用程序注意事项
  
## <a name="application-compatibility"></a>应用程序兼容性

要在 MultiPoint 服务系统上运行的任何应用程序都必须满足以下要求：
  
- 它应在 Windows Server 2016 上安装并运行 
- 它需要是会话感知，因此每个用户都可以在 MultiPoint 系统中运行该应用程序的实例。
  
如果应用程序指定了此要求，我们建议尝试安装该应用程序并将其用于远程桌面会话。 

## <a name="addressing-application-compatibility-problems"></a>解决应用程序兼容性问题  
MultiPoint 服务提供将工作站与完全在同一台主机上运行的 Windows 10 企业版版本关联的选项。 对于不会为多个用户运行多个实例的关键应用程序，或者不会在64位操作系统上安装，这可能是一个解决方案。 以这种方式部署桌面需要使用 MultiPoint Manager 中的 "虚拟桌面" 选项卡执行以下操作：  
  
-   启用虚拟桌面  
-   创建桌面模板  
-   通过问题应用程序自定义模板  
-   将工作站与自定义模板关联  

每个工作站都从同一模板开始，因此，每次计算机启动时都会清除所有更改。  
  
>[!NOTE] 
>务必验证要在 MultiPoint 上运行的应用程序的许可要求。 尽管你要安装一个复制应用程序，但可能需要每用户许可。  
  
