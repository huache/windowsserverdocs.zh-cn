---
title: 使用 Windows Server Essentials ADK 的重要信息
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 26cb2992-1250-4672-98ee-8b870baa45d5
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: a7fc10eb7c04163ca3202e481df130fc86f3c49c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623502"
---
# <a name="important-information-for-using-the-windows-server-essentials-adk"></a>使用 Windows Server Essentials ADK 的重要信息

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

若要创建和自定义 Windows Server Essentials 的映像，请使用 [windows 8 adk](https://go.microsoft.com/fwlink/?LinkId=248647)中的许多工具，但是 WINDOWS 8 Adk 和 Windows SERVER Essentials ADK 之间存在一些重要的差异。

 应注意以下重要区别：

-   某些设置已在 **%windir%\setup\script\SetupComplete.cmd** 中进行了更改。 如果要使用此命令，则可以添加其他命令行，但不删除现有行。

## <a name="working-with-passwords"></a>使用密码

-   管理员的密码设置为 Admin@123 ，并且在 Install.wim\unattend.xml 中启用了自动登录。 因此，无需在服务器初始配置过程中多次重新键入密码。 如果在可移动媒体的根目录中有自定义的 unattend.xml 文件，则会覆盖此设置，并且你需要设置密码，然后在启动时登录.

-   在初始配置期间，系统会提示最终用户创建新帐户和密码。 此新帐户将成为操作系统的网络管理员帐户。 然后管理员帐户和自动登录将被禁用。 可以使用 cfg.ini 文件自动完成此过程从而执行质量保证测试。

-   有关创建 unattend.xml 文件的详细信息，请参考 [Windows 8 ADK](https://go.microsoft.com/fwlink/?LinkId=248694) 文档。

## <a name="see-also"></a>另请参阅

 [入门 Windows Server ESSENTIALS ADK](Getting-Started-with-the-Windows-Server-Essentials-ADK.md) [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)

