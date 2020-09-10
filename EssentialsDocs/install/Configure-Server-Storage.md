---
title: 配置服务器存储
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: ef7ddcdd-3a74-40ca-9487-c3a6fc5155a5
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: be4bf42f2fe287ad6bd96b9ea5735147ec253e0d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621832"
---
# <a name="configure-server-storage"></a>配置服务器存储

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

## <a name="sample-hard-disk-configurations"></a>示例硬盘配置
 下表给出了示例硬盘配置的建议。 估计值基于典型用途和功能，但不说明影响最佳性能的问题。 你可以根据客户的喜好和需要对这些配置（如 SATA 或 SCSI）使用任意类型的受支持硬盘。

> [!IMPORTANT]
>   Windows Server Essentials 必须安装为 C：卷，并且卷大小必须至少为 60 GB。 建议在操作系统磁盘上创建两个分区，并且不使用 C:（系统分区）存储任何业务数据。

|服务器级别|磁盘配置|
|------------------|------------------------|
|条目|-两个物理磁盘<br /><br /> -配置为 RAID 1 镜像集，其中包含以下内容：<br /><br /> -C：卷？ 60 GB<br /><br /> -D：卷？ 1000 GB|
|中|-三个物理磁盘<br /><br /> -配置为 RAID 5 集，其中包含以下内容：<br /><br /> -C：卷？ 60 GB<br /><br /> -D：卷？ 1500 GB|
|高|-5 个或更多物理磁盘总数<br /><br /> -第两个磁盘位于 RAID 1 镜像集内，其中包含 C：卷？ 100 GB<br /><br /> -RAID 5 集中的所有剩余磁盘，其中包含以下内容：<br /><br /> -D：卷？ 1500 GB<br /><br /> -E：卷？ 1500 GB|

 这些建议考虑到已安装的操作系统的大小、服务器使用的数据存储的平均大小，以及在服务器的整个生命周期内预期的数据存储增长情况。 卷可以是单个物理磁盘上的分区，也可以置于单独的物理磁盘上。 由于服务器存储客户的重要数据，因此建议你使用多个物理磁盘并使用硬件 RAID 或存储空间来帮助保护客户的数据。

## <a name="configuring-your-server-backup"></a>配置服务器备份
 除了服务器上的内部硬盘以外，客户还应考虑使用 USB 移动硬盘进行备份。 理想情况下，客户应至少有两个移动硬盘，其容量足以备份服务器上的所有数据。 如果使用移动硬盘，则客户可以每晚将一个硬盘带离现场，以进一步保护数据。

## <a name="partition-configuration"></a>分区配置
 在服务器的初始配置过程中，会在磁盘 0 上最大的数据分区中创建包含共享文件夹和客户端计算机备份文件夹的默认服务器文件夹集。

## <a name="see-also"></a>另请参阅

 [入门 Windows Server ESSENTIALS ADK](Getting-Started-with-the-Windows-Server-Essentials-ADK.md) [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)

