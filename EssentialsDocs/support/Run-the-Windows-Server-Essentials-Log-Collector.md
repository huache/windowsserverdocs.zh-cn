---
title: 运行 Windows Server Essentials 日志收集器
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: 0d340223-fa24-4c75-ba8e-b654feb120ab
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 6aac2ed382321349d39874c7db7617f6da845919
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80852270"
---
# <a name="run-the-windows-server-essentials-log-collector"></a>运行 Windows Server Essentials 日志收集器
你可以从服务器或网络上的计算机运行 Windows Server Essentials 日志收集器。 如果你从服务器运行日志收集器，则仅可以从该服务器收集日志。 如果你从网络计算机运行日志收集器，则除了该计算机的日志之外，你还可以选择从该服务器收集日志。  
  
 你必须具有相应的管理权限才能运行日志收集器。 如果你收集服务器的日志文件，则你必须是服务器管理员；如果你收集网络计算机上的日志文件，则你必须是该计算机的客户端管理员。  
  
#### <a name="to-run-the-log-collector-on-the-server-by-using-the-wizard"></a>使用向导在服务器上运行日志收集器的步骤  
  
1. 在服务器的 "**开始**" 页上，单击 " **Windows Server Essentials 日志收集器**"。  
  
   > [!NOTE]
   > - 如果日志收集器程序未出现在 "**开始**" 页上，请浏览到 " **%system%\program files Files （X86） \Windows Server Essentials 日志收集器**"，然后双击 " **LogCollector**"。  
   >   -   如果你未使用管理权限登录到该服务器，则日志收集器将提示你输入你的凭据。  
  
2. 当系统提示你提供保存所收集的日志文件的位置时，可以选择默认位置， **\\\\< ServerName\>\logs**，或指定其他位置。 若要接受默认位置，请单击 **“下一步”** 。 若要更改位置，请单击 **“浏览”** ，导航到要保存日志文件的文件夹，然后单击 **“保存”** 。  
  
   > [!NOTE]
   >  你无需提供日志文件的文件名。 日志收集器通过连接计算机名称和文件的时间戳来命名 zip 文件集合。  
  
3. 收集日志时将显示进度栏。  
  
4. 若要查看日志集文件的内容，请选中 **“打开保存日志的文件位置”** 复选框，然后单击 **“关闭”** 以关闭向导并打开日志集合文件。  
  
#### <a name="to-run-the-log-collector-on-a-network-computer-by-using-the-wizard"></a>使用向导在网络计算机上运行日志收集器的步骤  
  
1.  浏览到 " **%System%\program files Files （x86） \Windows Server Essentials 日志收集器**"，然后双击 " **LogCollector**" 文件。  
  
    > [!NOTE]
    >  如果你未使用管理权限登录到网络计算机，请在收到提示时输入用户名和密码，然后单击 **“下一步”** 。  
  
2.  选择你要收集的日志，如下所示：  
  
    1.  选中 **“服务器日志文件”** 复选框以收集服务器上的日志文件。  
  
    2.  默认选中 **“客户端计算机日志文件(此计算机)”** 复选框，指示日志收集器将从运行的网络计算机收集日志。 如果你只希望收集服务器日志，请清除 **“客户端计算机日志文件(此计算机)”** 复选框。  
  
    3.  单击 **“下一步”** 。  
  
3.  当收到提示时，请键入服务器管理员的用户名和密码，然后单击 **“下一步”** 。  
  
4.  键入或浏览到要保存日志文件的位置，然后单击 **“下一步”** 。  
  
    > [!NOTE]
    >  你无需提供日志文件的文件名。 日志收集器通过连接计算机名称和文件的时间戳来命名 zip 文件集合。  
  
5.  收集日志时将显示进度栏。  
  
6.  若要查看日志集文件的内容，请选中 **“打开保存日志的文件位置”** 复选框，然后单击 **“关闭”** 以关闭向导并打开日志集合文件。  
  
### <a name="running-the-log-collector-manually"></a>手动运行日志收集器  
 安装日志收集器后，将创建计划任务以运行该工具。 随后你可以从 **“计划任务管理器”** 运行日志收集器，而无需使用向导（如果启动向导时遇到问题）。  
  
##### <a name="to-manually-run-the-log-collector-on-the-server"></a>在服务器上手动运行日志收集器的步骤  
  
1.  直接或远程登录到服务器。  
  
2.  打开 **“任务计划程序”** 。  
  
3.  在 **“任务计划程序库”** 的根目录中，浏览到名为 **“LogCollector”** 的计划任务。  
  
4.  右键单击 **“LogCollector”** ，然后单击 **“运行”** 。 日志收集器会将日志放置在服务器上的默认文件夹中， **\\\\< ServerName\>\Logs**。 如果对该文件夹没有写入权限，或者该文件夹不存在，则会将日志置于 **< temp\>** 子目录中。  
  
##### <a name="to-manually-run-the-log-collector-on-a-network-computer"></a>在网络计算机上手动运行日志收集器的步骤  
  
1.  直接或远程登录到网络计算机。  
  
2.  打开 **“任务计划程序”** 。  
  
3.  在 **“任务计划程序库”** 的根目录中，浏览到名为 **“LogCollector”** 的计划任务。  
  
4.  右键单击 **“LogCollector”** ，然后单击 **“运行”** 。 日志收集器会将日志放置在网络计算机上 **< temp\>** 文件夹中。
