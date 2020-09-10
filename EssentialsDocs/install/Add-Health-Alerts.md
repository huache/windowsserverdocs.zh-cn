---
title: 添加运行状况警报
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 270e0aac-dc42-46f3-a20b-a68ffbded06d
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 3a3c04a48e06ef0040943b866eaf1ddb0be8fa89
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624071"
---
# <a name="add-health-alerts"></a>添加运行状况警报

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

运行状况加载项为警报、运行状况检查和网络问题修复提供了定义。 运行状况加载项包含一些 xml 文件，可注释用于评估特定功能的运行状况信息的代码或数据。 运行状况加载项由开发人员创建，由管理员安装在服务器和客户端计算机上。

 有关创建运行状况加载项的详细信息，请参考 [Windows Server Solutions SDK](https://go.microsoft.com/fwlink/?LinkID=248648) （Windows Server 解决方案 SDK）。

## <a name="installing-health-add-in-files"></a>安装运行状况加载项文件
 开发人员创建 XML 文件后，必须在服务器和客户端计算机上的适当位置放置这些文件的副本。

#### <a name="to-install-the-xml-files-on-the-server"></a>在服务器上安装 xml 文件

1. 在 **%ProgramFiles%\Windows Server\Bin\Feature Definitions** 文件夹中，创建一个名为 **MyHealthAddIn**的新文件夹。 可以为此文件夹指定任何名称。 建议为该文件夹指定与功能名称相同的名称。

2. 将 Definition.xml 和 Definition.xml.config 文件复制到该新文件夹中。

3. 如果已创建用于条件或操作的二进制文件，则还应将这些文件复制到 **%ProgramFiles%\Windows Server\Bin**。

   客户端计算机每隔 6 小时运行一次计划任务，将 XML 文件放置到适当的位置。 你可以通过手动运行任务强制执行客户端计算机和服务器之间的同步操作。

#### <a name="to-install-the-xml-files-on-the-client-computer"></a>在客户端计算机上安装 xml 文件

1.  打开任务计划程序。

2.  在任务计划程序中运行 **HealthDefintionUpdateTask**。

    > [!NOTE]
    >  此任务不能安装二进制文件。 必须手动将二进制文件复制到客户端计算机上的 **%ProgramFiles%\Windows Server\Bin** 文件夹。

## <a name="see-also"></a>另请参阅
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)