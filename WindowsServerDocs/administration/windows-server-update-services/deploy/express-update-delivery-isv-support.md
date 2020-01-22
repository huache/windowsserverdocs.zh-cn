---
title: Express 更新交付 ISV 支持
description: Windows Server Update Service (WSUS) 主题 - 独立软件供应商 (ISV) 如何使用 WSUS 配置 Express 更新交付
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-wsus
ms.tgt_pltfrm: na
ms.topic: get-started article
author: sakitong
ms.author: coreyp
manager: lizapo
ms.date: 10/16/2017
ms.openlocfilehash: 13568bb320a3d70bfd6a70d2b9731b460be6f346
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2020
ms.locfileid: "75948494"
---
# <a name="express-update-delivery-isv-support"></a>Express 更新交付 ISV 支持

>适用于：Windows 10、Windows Server 2016

Windows 10 更新下载可能会很大，因为每个包都包含以前发布的所有修复以确保一致性和简单性。  

从版本 7 开始，Windows 已能够通过称为 [Express](https://technet.microsoft.com/library/cc708456(v=ws.10).aspx#Anchor_2) 的功能减小 Windows 更新下载的大小，虽然使用者设备默认情况下支持该功能，但是 Windows 10 企业版设备需要具有 Windows Server Update Services (WSUS) 才能利用 Express。

## <a name="how-microsoft-supports-express"></a>Microsoft 如何支持 Express

- **独立 WSUS 上的 Express**

    Express 更新交付已在[所有受支持的 WSUS 版本上可用](https://technet.microsoft.com/library/cc708456(v=ws.10).aspx)。

- **直接连接到 Windows 更新的设备上的 Express** 

    使用者设备支持 Express 下载：它们使用 Windows 更新 (WU) 客户端来扫描、下载和安装更新。 在下载阶段中，WU 客户端请求 Express 包并下载合适的字节范围。

-  **使用[适用于企业的 Windows 更新](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)管理的企业设备**也可受益于 Express 更新传递支持，而无需对配置进行任何更改。

## <a name="how-isvs-can-take-advantage-of-express"></a>ISV 如何利用 Express

ISV 可以使用 WSUS 和 WU 客户端来支持 Express 更新交付。 Microsoft 建议执行以下三个步骤，下面的部分更详细地讨论了每个步骤：

1.  [**配置 WSUS**](#BKMK_1)

    WSUS 服务器是扫描和更新同步所必需的（可在[此处](https://technet.microsoft.com/library/dn800972(v=ws.11).aspx)找到更多信息）

2.  [**指定和填充 ISV 文件缓存**](#BKMK_2)

    建议使用 ISV 文件缓存来托管更新内容，其中包括更新 Cabinet 文件（.cab 文件）和 Express 包（.psf 文件）。

3.  [**设置 ISV 客户端代理来定向 WU 客户端操作**](#BKMK_3)

>[!NOTE]
>需要安装 Windows 10 版本 1607 的累积更新（2017 年 1 月或之后的）（[KB3213986（OS 内部版本 14393.693）](https://support.microsoft.com/help/4009938/january-10-2017-kb3213986-os-build-14393-693)。
    
   - ISV 客户端代理确定要批准哪些更新，以及何时下载和安装更新
   - WU 客户端确定要下载的字节范围并发起下载请求

### <a name="BKMK_1"></a>步骤 1：配置 WSUS

WSUS 充当 Windows 更新的接口，并管理描述了需要下载的 Express 包的所有元数据。 如果需要进行部署，请参阅 [**Windows Server Update Services 3.0 SP2 概述**](https://technet.microsoft.com/library/dd939931(v=ws.10).aspx)。 部署 WSUS 后，需要考虑的主要事项为是否将更新内容存储在 WSUS 服务器本地。 配置 WSUS 时，我们建议不要将更新存储在本地。 这假设你的环境中已有定向这些包的部署的软件。 有关如何配置 WSUS 本地存储的详细信息，请参阅[**决定在何处存储更新**](https://technet.microsoft.com/library/cc720494(v=ws.10).aspx)。

### <a name="BKMK_2"></a>步骤 2：指定和填充 ISV 文件缓存 

#### <a name="specify-the-isv-file-cache"></a>指定 ISV 文件缓存

[**配置服务提供商参考**](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference)中详述的新的客户端组策略和移动设备管理 (MDM) 设置定义了 ISV 文件缓存的位置。

| **名称**                                              | **描述**                                                                                                                                                      |
|-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 配置备用的更新下载位置。 | 指定备用 Intranet 服务器，用于托管来自 Microsoft 更新的更新。 然后，你可以使用此更新服务自动更新你的网络上的计算机。 |

设置 ISV 文件缓存的备用下载位置时有两个选项：

1. **指定 ISV HTTP 服务器主机名**，这是 ISV 文件缓存
    
    此方法将 WU 客户端配置为向策略中指定的 HTTP 服务器发出下载请求

2. **指定 localhost**
 
    此方法将 WU 客户端配置为向 localhost 发出下载请求。 这允许 ISV 客户端代理处理这些请求并根据情况进行路由来满足下载请求。

> [!IMPORTANT]
> ISV 文件缓存需要以下各项：                                                          
> - 根据 RFC，服务器必须符合 HTTP 1.1：<http://www.w3.org/Protocols/rfc2616/rfc2616.html>                                                                                                                                                                
> 具体而言，Web 服务器需要支持                                                                                                                                                                                                                                       [**HEAD**](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) 和 [**GET**](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.htm) 请求<br>                                                                                                                                                                                                                                                                                                  - 部分范围请求<br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   - Keep-alive<br>                                                                                                                                                                                                                                                                                                                                                                                                                            - 不要使用“Transfer-Encoding:chunked”                                                                                                 

#### <a name="populate-the-isv-file-cache"></a>填充 ISV 文件缓存

必须使用与要在托管客户端上安装的更新关联的文件来填充 ISV 文件缓存。 

**若要填充 ISV 文件缓存，请执行以下步骤：**

1. 使用 [WSUS API](https://msdn.microsoft.com/library/windows/desktop/microsoft.updateservices.administration.updatefile(v=vs.85).aspx) 访问 MU 服务的更新的文件路径和名称。

    WSUS 服务器上的每个更新的元数据包含该更新在 Microsoft 更新上的文件路径和文件名（Microsoft 更新主机名为粗体，后跟文件路径和文件名）： **<http://download.windowsupdate.com>** /c/msdownload/update/software/updt/2016/09/windows10.0-kb3195781-x64_0c06079bccc35cba35a48bd2b1ec46f818bd2e74.msu

2. 从 Microsoft 更新下载文件，并使用以下两种方法之一将文件存储在 ISV 文件缓存中： 

   - 使用**与 MU 服务上相同的文件夹路径**来存储文件

   - 使用 **ISV 定义的文件夹路径**来存储文件

     让 HTTP 服务器（或 localhost）将 **HTTP GET** 请求（它们引用 MU 文件夹路径和文件名）重定向到 ISV 文件位置。

### <a name="BKMK_3"></a>步骤 3：设置 ISV 客户端代理来定向 WU 客户端操作

ISV 客户端代理使用以下建议的工作流来安排已批准更新的下载和安装：

1.  ISV 客户端代理调用 WU 客户端来扫描 WSUS 服务器

2.  扫描将适用的更新集返回给 WU 客户端

3.  ISV 客户端确定要批准、下载和安装哪些更新

4.  ISV 客户端代理调用 WU 客户端来下载已批准的更新

5.  下载更新后，ISV 客户端代理将调用 WU 客户端来安装已批准的更新

有关使用 WU 客户端来扫描、下载和安装更新的其他信息，请参阅[搜索、下载和安装更新](https://msdn.microsoft.com/library/windows/desktop/aa387102(v=vs.85).aspx)。

### <a name="download-workflow-options"></a>下载工作流选项

下面是使用 ISV 文件缓存的下载工作流选项的两个插图：

![工作流 1](../../media/express-update-delivery-isv-support/image1.png)

![工作流 2](../../media/express-update-delivery-isv-support/image2.png)
### <a name="how-express-download-works"></a>Express 下载的工作方式

- 对于支持 Express 的 OS 更新，服务上存储了两个版本的文件有效负载：

  - **完整文件版本** - 从根本上替换更新二进制文件的本地版本。

  - **Express 版本** - 包含修补设备上的现有二进制文件所需的增量。 

    在扫描阶段中已下载到客户端的更新元数据中会同时引用完整文件版本和 Express 版本。 

    **Express 下载的工作方式如下所述：**

    WU 客户端会首先尝试下载 Express，某些情况下会在需要时回退到完整文件（例如，如果经过不支持字节范围请求的代理）。

  1. WU 客户端发起 Express 下载时，**WU 客户端会首先下载一个存根**，这是 Express 包的一部分。

  2. **WU 客户端将此存根传递给 Windows Installer**，后者会使用此存根进行本地清查（将设备上的文件的增量与访问所提供的最新文件版本所需的内容进行比较）。

  3. **Windows Installer 随后请求 WU 客户端下载**已确定的必需范围。

  4. **WU 客户端会下载这些范围并将它们传递给 Windows Installer**，后者会应用这些范围，然后确定是否需要其他范围。 此过程会一直重复，直到 Windows Installer 告知 WU 客户端所有必需范围都已下载。

  此时，下载已完成，更新已准备好进行安装。

### <a name="how-delivery-optimization-reduces-bandwidth-consumption"></a>交付优化如何降低带宽消耗

交付优化 (DO) 是一种自我组织的分布式缓存解决方案，适用于希望降低操作系统更新、操作系统升级和应用程序所需带宽消耗的企业。 DO 允许客户端从备用源（例如网络上的其他对等方）以及指定的下载位置（在此场景中为 ISV 文件缓存）下载那些元素。

默认情况下，在 Windows 10 企业版和教育版中，交付优化仅允许在组织自有的网络中进行对等共享，但你可以使用组策略和移动设备管理 (MDM) 设置对其进行不同配置。

有关 DO 的详细信息，请参阅[配置适用于 Windows 10 更新的交付优化](https://technet.microsoft.com/itpro/windows/manage/waas-delivery-optimization)。
