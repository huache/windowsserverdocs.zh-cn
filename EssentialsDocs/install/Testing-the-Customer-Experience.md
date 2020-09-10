---
title: 测试客户体验
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 1b1a2040-4cfd-48bf-8d04-3ffde9c26b9b
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: c109fbd7ef2e4852e296f893ae8981ba8feeaed8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623333"
---
# <a name="testing-the-customer-experience"></a>测试客户体验

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

要检查客户体验并检查你的合作伙伴自定义情况，请对目标计算机运行初始配置。 建议你至少手动完成一次初始配置，以了解客户体验。 如果已为仪表板添加联合品牌，你必须完成初始配置以验证该品牌。 如果你添加联合品牌远程 Web 访问站点，则必须访问 http://<servername \> 来验证品牌 ( # B1 servername \> 是服务器) 的名称。 你可以使用 cfg.ini 文件的初始配置部分自动测试客户体验。 有关创建 cfg.ini 文件的此部分的详细信息，请参阅[创建 cfg.ini 文件](Create-the-Cfg.ini-File.md)。

> [!IMPORTANT]
>  必须在测试初始配置体验前运行 Sysprep.exe 命令来准备要部署的映像。 有关运行 Sysprep.exe 的详细信息，请参阅[准备要部署的映像](Preparing-the-Image-for-Deployment.md)。

> [!IMPORTANT]
>  若要测试初始配置，必须具有网络连接。 不要在服务器上配置或安装 DHCP，以便在没有干扰的情况下测试网络。

 要验证合作伙伴支持信息，请在仪表板中单击“帮助”按钮旁边的向下箭头。

## <a name="see-also"></a>另请参阅
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备要部署的映像](Preparing-the-Image-for-Deployment.md)