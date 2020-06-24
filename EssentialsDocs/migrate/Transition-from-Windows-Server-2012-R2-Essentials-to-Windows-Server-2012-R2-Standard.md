---
title: 从 Windows Server Essentials 转换到 Windows Server 2012 R2 Standard
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: a14689e3-2310-4229-bd3e-dafc0e739e02
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 145d4ef1039093f224e1dc73cb5d8286ddd8e494
ms.sourcegitcommit: fdc3ce1992f4dd6ea1771479d525126abbbcfa72
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85256477"
---
# <a name="transition-from-windows-server-essentials-to-windows-server-2012-r2-standard"></a>从 Windows Server Essentials 转换到 Windows Server 2012 R2 Standard

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

Windows Server 2016 是支持云的操作系统，它支持当前的工作负荷，同时引入新技术，使其易于过渡到云计算。 Windows Server 2016 内容帮助你做好准备工作。

 Windows Server Essentials 支持最多25个用户和50设备。 当你的业务需求超过限制时，你可以执行从 Windows Server Essentials 到 Windows Server 2012 R2 Standard 的就地许可转换，以保持许可证相容性。  
  
 转换到 Windows Server 2012 R2 Standard 后，用户帐户和设备限制将被删除，但 Windows Server Essentials 独有的功能（如仪表板、远程 Web 访问和客户端计算机备份）仍然可用。 但是，由于这些功能在技术上的限制，最多只能支持 100 个用户帐户和 200 台设备。 客户端计算机备份功能将支持最多 75 台设备的备份。  
  
> [!IMPORTANT]
>   Windows Server 2012 R2 标准版要求在您的环境中为每个用户或设备提供客户端访问许可证（CAL）。 这不同于 Windows Server Essentials，后者不使用 CAL 模式，也不包含任何 Cal。 从 Windows Server Essentials 转换到 Windows Server 2012 R2 Standard 时，需要为环境购买适当数量和类型的 Cal （大多数客户购买用户 Cal）。  
  
## <a name="before-the-transition"></a>转换前  
  
-   在从 Windows Server Essentials 转换到 Windows Server 2012 R2 Standard 之前，应该完全备份服务器数据。  
  
    > [!IMPORTANT]
    >  如果不完整备份服务器数据，则无法将服务器还原到转换前的状态。  
  
-   此外，请确保阅读并了解适用于 Windows Server 2012 R2 Standard 的最终用户许可协议（EULA）。 查看 EULA 的步骤：  
  
    1.  以管理员身份打开命令窗口。  
  
    2.  运行下面的命令：  
  
         **dism /online /set-edition:ServerStandard /geteula:** *eula path* （其中 *eula path* 表示要用于保存 EULA 文件的位置；例如：C:\ws8std_eula.rtf）。 请务必使用 .rtf 作为文件后缀名。  
  
    3.  打开保存该文件的位置，然后双击打开该文件。  
  
## <a name="transition-to--windows-server-2012-r2-standard"></a>转换到 Windows Server 2012 R2 Standard  
 确定从 Windows Server Essentials 转换到 Windows Server 2012 R2 Standard 后，请完成以下两个步骤：  
  
1. 购买适用于你的环境的 Windows Server 2012 R2 Standard 许可证以及适当数量的用户和/或设备客户端访问许可证。  
  
    你可以从零售输出口、分销商处购买 Windows Server 2012 R2 Standard 的许可证，也可以通过[Microsoft 合作伙伴](https://pinpoint.microsoft.com/SelectCulture.aspx)的帮助。  
  
   > [!NOTE]
   >  如果最初购买 Windows Server 2012 R2 Standard 并执行降级权限，将两个虚拟实例之一安装为 Windows Server Essentials，则无需再购买任何其他产品。  
   >   
   >  如果通过批量许可渠道购买 Windows Server 2012 R2 Standard，则可以从批量许可服务中心（VLSC）下载 ISO 映像和 Windows Server 2012 R2 Standard 的产品密钥。  
   >   
   >  如果从任何其他渠道购买 Windows Server 2012 R2 标准版，则可以从[TechNet 评估中心](https://technet.microsoft.com/evalcenter/jj659306.aspx)下载适用于 Windows server ESSENTIALS 的 ISO 映像和评估版产品密钥。 下一步中介绍的转换操作会将评估产品转换为完全授权和受支持的产品。  
  
2. 以管理员身份打开 Windows PowerShell，然后运行以下命令：  
  
    **dism/online/set-edition： ServerStandard/accepteula/productkey：** *产品密钥*（其中*产品密钥*是 Windows Server 2012 R2 Standard 副本的产品密钥）。  
  
    服务器将重新启动，完成转换过程。  
  
   转换后，Windows Server Essentials 功能将保留在服务器上，最多支持100用户和200设备。  
  
## <a name="see-also"></a>请参阅  
  

-   [将服务器数据迁移到 Windows Server Essentials](Migrate-Server-Data-to-Windows-Server-Essentials.md)

