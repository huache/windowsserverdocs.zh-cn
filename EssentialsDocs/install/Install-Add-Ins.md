---
title: 安装加载项
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: e62e4f07-c2ba-4c5e-b30c-bdc287cd654e
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 32bb6be1ff24823d628e23945849b5030d6e0723
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626326"
---
# <a name="install-add-ins"></a>安装加载项

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

可以在创建映像前，通过在所有服务器或客户端计算机上安装加载项来包括加载项。 之后，将在使用该映像复制的所有计算机上自动包括这些加载项。 你可以通过运行 .wssx 文件来安装加载项，也可以按照 [SDK 文档](https://go.microsoft.com/fwlink/?LinkID=248648)中关于各种加载项的指南来安装单独的加载项文件。 如果使用 .wssx 文件进行安装，则可以通过加载项管理器来卸载加载项。 如果安装单独的文件，则不能使用加载项管理器管理加载项。

> [!NOTE]
>  任何安装到或下载到服务器上的软件（包括仪表板选项卡和运行状况通知）都应该具有与此服务器上安装的操作系统的语言相匹配的本地化界面。

#### <a name="to-install-an-add-in"></a>安装加载项

1.  （可选）如果通过使用 .wssx 文件安装加载项，请完成下列步骤：

    1.  将 <Companyname.addinname \> . .wssx 文件保存在引用计算机上。

    2.  双击该 .wssx 文件打开“加载项安装向导”。

    3.  按照向导中的说明完成安装。

2.  （可选）按照 SDK 中针对各种加载项的定义，在适当的位置安装各个加载项文件。

## <a name="see-also"></a>另请参阅
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)