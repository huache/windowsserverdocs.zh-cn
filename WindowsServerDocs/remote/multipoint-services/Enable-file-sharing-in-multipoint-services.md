---
title: 启用文件共享
description: 了解 MultiPoint Services 中的文件共享
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.topic: article
ms.assetid: 508ad056-8e0c-4d59-a4fa-05775a54125d
author: evaseydl
ms.author: evas
manager: Scottman
ms.openlocfilehash: 73f89700228d912ac029a97dc3951be21a01e45a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80859260"
---
# <a name="enable-file-sharing-in-multipoint-services"></a>在 MultiPoint 服务中启用文件共享
可以通过两种方式允许 MultiPoint 工作站上的用户共享文件：  
  
-   **如果网络中有文件服务器，** 建议您在文件服务器上创建一个共享文件夹。  
  
-   **如果你的小型网络为2-3 多点服务器，但没有专用的文件服务器，** 则其中一个 multipoint 服务器可充当所有其他运行 multipoint 服务的计算机的文件服务器。 在该服务器上创建一个共享文件夹，然后为该服务器上的所有用户创建本地用户帐户。 共享文件夹可以位于原始内部驱动器上，也可以将其他内部或外部驱动器连接到计算机。  
  
