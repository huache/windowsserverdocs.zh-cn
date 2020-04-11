---
ms.assetid: e34622ff-b2d0-4f81-8d00-dacd5d6c215e
title: Windows 时间服务技术参考
author: dcuomo
ms.author: dacuo
manager: dougkim
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows-server
ms.technology: networking
ms.openlocfilehash: 51711d423582aee4ebc3762a51abe9156754b55a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80860130"
---
# <a name="windows-time-service"></a>Windows 时间服务

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows 10 或更高版本


**本指南中的内容**  
  
* 查找 Windows 时间服务配置信息的位置  
* 什么是 Windows 时间服务？  
* 时间协议的重要性  
* Windows 时间服务的工作原理   
* Windows 时间服务工具和设置  
  
> [!NOTE]  
> 在 Windows Server 2003 和 Microsoft Windows 2000 Server 中，目录服务被命名为 Active Directory 目录服务。 在 Windows Server 2008 R2 和 Windows Server 2008 中，目录服务被命名为 Active Directory 域服务 (AD DS)。 本主题的其余部分引用的名称是 AD DS，但该信息还适用于 Windows Server 2016 中的 Active Directory 域服务。  
  
Windows 时间服务（也称为 W32Time）同步在 AD DS 域上运行的所有计算机的日期和时间。 对于许多 Windows 服务和业务线应用程序的正确操作，时间同步至关重要。 Windows 时间服务使用网络时间协议 (NTP) 来同步网络上的计算机时钟，以便可以将准确的时钟值或时间戳分配给网络验证和资源访问请求。 该服务可集成 NTP 和时间提供程序，使其成为企业管理员的可靠和可缩放的时间服务。
  
> [!IMPORTANT]  
> 在 Windows Server 2016 之前，W32Time 服务并不是为了满足时间敏感型应用程序的需要。  但是，通过 Windows Server 2016 的更新，现在可以在域中实施可达到 1 毫秒准确性的解决方案。  有关详细信息，请参阅 [Windows 2016 精确时间](accurate-time.md)和[用于针对高精度环境配置 Windows 时间服务的支持边界](support-boundary.md)。  
  
## <a name="where-to-find-windows-time-service-configuration-information"></a><a name="BKMK_Config"></a>查找 Windows 时间服务配置信息的位置  
本指南不讨论如何配置 Windows 时间服务  。 Microsoft TechNet 和 Microsoft 知识库中有多个不同的主题，它们解释了配置 Windows 时间服务的过程。 如果你需要配置信息，以下主题应该可帮助你找到相应的信息。  
  
-   若要为目录林根级主域控制器 (PDC) 模拟器配置 Windows 时间服务，请参阅：  
  
    -   [在目录林根级域中的 PDC 模拟器上配置 Windows 时间服务](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731191%28v=ws.10%29) 
  
    -   [配置林的时间源](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc794823%28v%3dws.10%29) 
  
    -   Microsoft 知识库文章 816042，[如何在 Windows Server 中配置权威时间服务器](https://go.microsoft.com/fwlink/?LinkID=60402)，这篇文章介绍了运行 Windows Server 2008 R2、Windows Server 2008、Windows Server 2003 和 Windows Server 2003 R2 的计算机的配置设置。  
  
-   若要在任何域成员客户端或服务器上配置 Windows 时间服务，或甚至在未配置为目录林根级 PDC 模拟器的域控制器上进行配置，请参阅[配置客户端计算以进行自动域时间同步](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc816884%28v%3dws.10%29)。  
  
    > [!WARNING]  
    > 某些应用程序可能要求计算机具有高准确度的时间服务。 如有必要，可以选择配置手动时间源，但是请注意，Windows 时间服务并不是专为作为高精度时间源而设计的。 请确保了解 Microsoft 知识库文章 939322 [用于针对高精度环境配置 Windows 时间服务的支持边界](support-boundary.md)中所述的适用于高精度环境的支持限制。  
  
-   若要在任何基于 Windows 的客户端或配置为工作组成员而非域成员的服务器计算机上配置 Windows 时间服务，请参阅[为所选客户端计算机配置手动时间源](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc816656%28v%3dws.10%29)。  
  
-   若要在运行虚拟环境的托管计算机上配置 Windows 时间服务，请参阅 Microsoft 知识库文章 816042 [如何在 Windows Server 中配置权威时间服务器](https://go.microsoft.com/fwlink/?LinkID=60402)。 如果使用的是非 Microsoft 虚拟化产品，请务必查阅关于该产品的供应商文档。  
  
-   若要在运行于虚拟机中的域控制器上配置 Windows 时间服务，建议在主机系统和充当域控制器的来宾操作系统之间禁用部分时间同步。 通过此操作，来宾域控制器将能够同步域层次结构的时间，还可以防止此控制器从“已保存”状态还原时出现时间偏差。 有关详细信息，请参阅 Microsoft 知识库文章 976924 [收到虚拟化域控制器（通过 Hyper-V 在基于 Windows Server 2008 的主机服务器上运行）上的 Windows 时间服务事件 ID 24、29 和 38](https://go.microsoft.com/fwlink/?LinkID=192236) 和[虚拟化域控制的部署注意事项](https://go.microsoft.com/fwlink/?LinkID=192235)。  
  
-   若要在充当目录林根级 PDC 模拟器且在虚拟计算机上运行的域控制器中配置 Windows 时间服务，请按照[在目录林根级域中的 PDC 模拟器上配置 Windows 时间服务](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731191%28v=ws.10%29)中所述的针对物理计算机的相同说明进行操作。  
  
-   若要在作为虚拟计算机运行的成员服务器上配置 Windows 时间服务，请使用[配置客户端计算以进行自动域时间同步](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc816884%28v%3dws.10%29)中所述的域时间层次结构。  
  
## <a name="what-is-the-windows-time-service"></a><a name="BKMK_WTS"></a>什么是 Windows 时间服务？  
Windows 时间服务 (W32Time) 为计算机提供网络时钟同步，而无需进行大量配置。  
  
Windows 时间服务对于成功运行 Kerberos 版本 5 身份验证非常重要，因此对于基于 AD DS 的身份验证也很重要。 任何 Kerberos 感知应用程序（包括大多数安全服务）都依赖于加入身份验证请求的计算机之间的时间同步。 AD DS 域控制器也必须具有同步的时钟，以帮助确保精确的数据复制。  
  
Windows 时间服务在名为 W32Time.dll 的动态链接库中实现。 W32Time.dll 在操作系统设置和安装期间默认安装在 %Systemroot%\System32 文件夹中  。  
  
W32Time.dll 最初是为 Windows 2000 Server 开发的，用于支持 Kerberos V5 身份验证协议所要求的规范，该协议要求同步网络上的时钟。 从 Windows Server 2003 开始，W32Time.dll 通过 Windows 2000 Server 操作系统提高了网络时钟同步的准确度，此外，还通过时间提供程序支持各种硬件设备和网络时间协议。 尽管最初旨在为 Kerberos 身份验证提供时钟同步，但当前许多应用程序都使用时间戳以确保事务一致性，并记录重要事件的时间以及其他业务关键型、时间敏感型信息。 这些应用程序受益于 Windows 时间服务提供的计算机之间的时间同步。  
  
## <a name="importance-of-time-protocols"></a><a name="BKMK_TimeProtocols"></a>时间协议的重要性  
时间协议在两台计算机之间进行通信以交换时间信息，然后使用该信息同步其时钟。 使用 Windows 时间服务时间协议，客户端可以从服务器请求时间信息，并根据收到的信息同步其时钟。  
  
Windows 时间服务使用 NTP 来帮助同步网络上的时间。 NTP 是一种 Internet 时间协议，其中包括同步时钟所需的约束算法。 NTP 是比某些 Windows 版本中使用的简单网络时间协议 (SNTP) 更准确的时间协议；但是，W32Time 继续支持 SNTP，以便能够与运行基于 SNTP 的时间服务（例如 Windows 2000）的计算机后向兼容。  
  
## <a name="see-also"></a>另请参阅  
[Windows 时间服务的工作原理](How-the-Windows-Time-Service-Works.md)  
[Windows 时间服务工具和设置](Windows-Time-Service-Tools-and-Settings.md)  
[Microsoft 知识库文章 902229](https://go.microsoft.com/fwlink/?LinkId=186066)