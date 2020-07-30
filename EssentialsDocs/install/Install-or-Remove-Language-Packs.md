---
title: 安装或删除语言包
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 98f13f63-4480-40ba-a7ef-d1d9b7582e5f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: fa167ec12122883fc0ccea914260407d13f0b992
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181163"
---
# <a name="install-or-remove-language-packs"></a>安装或删除语言包

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

> [!NOTE]
>  添加 Windows Server Essentials 语言包之前，必须先按照[语言包和部署](https://technet.microsoft.com/library/hh824829)中的说明创建多语言 Windows 映像。

 语言包只能用于创建多语言映像。 本部分中的信息特定于在 Windows Server Essentials 上安装或删除语言包。

> [!NOTE]
>  如果要从不支持东亚语言（如 ja-jp）的客户端计算机运行初始配置 (IC)，并且服务器的多语言映像中不包括英语，则 IC 网页将显示方块。 要使 IC 网页默认为英语，则创建的多语言映像必须包括英语。

## <a name="adding-language-packs-to-an-image"></a>向映像中添加语言包
 语言包可以在 OEM 自定义 DVD 上获取。 建议你在向映像添加语言包之前先将语言包复制到你的技术人员计算机中。

 若要安装语言包，你必须使用以下命令：

 **dism.exe/online/Add-Package/PackagePath： C： \\<cab 文件目录的完整路径 \>\lp.cab**

 例如，以下命令显示了如何添加德语语言包：

 **dism.exe /online /Add-Package /PackagePath:C:\Users\Administrator\Desktop\WindowsHomeServer-Product-r\de-de\lp.cab**

> [!IMPORTANT]
>  还必须为 Windows Server Essentials 应用语言包以完整本地化操作系统。

## <a name="removing-language-packs-from-an-image"></a>从映像中删除语言包
 你可以使用以下命令删除不再需要包含在映像中的语言包：

 **dism.exe/online/Remove-Package/PackagePath： C： \\<cab 文件目录的完整路径 \>\lp.cab**

 例如，以下命令显示了如何删除德语语言包：

 **dism.exe /online /Remove-Package /PackagePath:C:\Users\Administrator\Desktop\WindowsHomeServer-Product-r\de-de\lp.cab**

## <a name="see-also"></a>另请参阅

 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)

