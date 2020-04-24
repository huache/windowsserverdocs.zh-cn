---
title: 部署具有高可用性的 Windows Admin Center
description: 部署具有高可用性的 Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 6ae7bd9ed7aee5835ac1f53b9e10879ad8824f52
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "71406946"
---
# <a name="deploy-windows-admin-center-with-high-availability"></a>部署具有高可用性的 Windows Admin Center

>适用于：Windows Admin Center、Windows Admin Center 预览版

可以在故障转移群集中部署 Windows Admin Center，为 Windows Admin Center 网关服务提供高可用性。 提供的解决方案是一种主动-被动解决方案，其中只有一个 Windows Admin Center 实例处于活动状态。 如果群集中的某个节点发生故障，Windows Admin Center 会正常故障转移到另一个节点，从而使你可以无缝继续管理环境中的服务器。 

[了解其他 Windows Admin Center 部署选项。](../plan/installation-options.md)

## <a name="prerequisites"></a>必备条件

- Windows Server 2016 或 2019 上 2 个或多个节点的故障转移群集。 [详细了解如何部署故障转移群集](../../../failover-clustering/failover-clustering-overview.md)。
- 适用于 Windows Admin Center 的群集共享卷 (CSV)，用于存储群集中所有节点可访问的永久性数据。 对于你的 CSV，10 GB 就足够了。
- [Windows Admin Center HA 脚本 zip 文件](https://aka.ms/WACHAScript)中的高可用性部署脚本。 下载包含本地计算机脚本的 .zip 文件，然后根据需要按照以下指南复制脚本。
- 推荐但可选用：签名证书 .pfx 和密码。 无需提前在群集节点上安装此证书，该脚本将执行此操作。 如果未提供证书，该安装脚本会生成自签名证书，该证书将在 60 天后过期。

## <a name="install-windows-admin-center-on-a-failover-cluster"></a>在故障转移群集上安装 Windows Admin Center

1. 将 ```Install-WindowsAdminCenterHA.ps1``` 脚本复制到群集中的节点。 下载 Windows Admin Center .msi，或将其复制到相同的节点。
2. 通过 RDP 连接到节点，并通过以下参数从该节点运行 ```Install-WindowsAdminCenterHA.ps1``` 脚本：
    - `-clusterStorage`：用于存储 Windows Admin Center 数据的群集共享卷的本地路径。
    - `-clientAccessPoint`：选择将用于访问 Windows Admin Center 的名称。 例如，如果使用参数 `-clientAccessPoint contosoWindowsAdminCenter` 运行该脚本，则将通过访问 `https://contosoWindowsAdminCenter.<domain>.com` 来访问 Windows Admin Center 服务
    - `-staticAddress`：可选。 群集通用服务的一个或多个静态地址。 
    - `-msiPath`：Windows Admin Center .msi 文件的路径。
    - `-certPath`：可选。 证书 .pfx 文件的路径。
    - `-certPassword`：可选。 `-certPath` 中提供的证书 .pfx 的 SecureString 密码
    - `-generateSslCert`：可选。 如果不想提供签名证书，请包含此参数标志以生成自签名证书。 请注意，自签名证书将于 60 天后过期。
    - `-portNumber`：可选。 如果未指定端口，则将在端口 443 (HTTPS) 上部署网关服务。 若要使用其他端口，请在此参数中指定。 请注意，如果使用自定义端口（除 443 之外的任何端口），将通过访问 https://\<clientAccessPoint\>:\<port\> 来访问 Windows Admin Center。

> [!NOTE]
> ```Install-WindowsAdminCenterHA.ps1``` 脚本支持 ```-WhatIf ``` 和 ```-Verbose``` 参数

### <a name="examples"></a>示例

#### <a name="install-with-a-signed-certificate"></a>使用签名证书安装：

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -clusterStorage "C:\ClusterStorage\Volume1" -clientAccessPoint "contoso-ha-gateway" -msiPath ".\WindowsAdminCenter.msi" -certPath "cert.pfx" -certPassword $certPassword -Verbose
```

#### <a name="install-with-a-self-signed-certificate"></a>使用自签名证书安装：

```powershell
.\Install-WindowsAdminCenterHA.ps1 -clusterStorage "C:\ClusterStorage\Volume1" -clientAccessPoint "contoso-ha-gateway" -msiPath ".\WindowsAdminCenter.msi" -generateSslCert -Verbose
```

## <a name="update-an-existing-high-availability-installation"></a>更新现有的高可用性安装

使用相同的 ```Install-WindowsAdminCenterHA.ps1``` 脚本更新 HA 部署，不会丢失连接数据。

### <a name="update-to-a-new-version-of-windows-admin-center"></a>升级到新版本的 Windows Admin Center

发布新版本的 Windows Admin Center 时，只需使用 ```msiPath``` 参数再次运行 ```Install-WindowsAdminCenterHA.ps1``` 脚本：

```powershell
.\Install-WindowsAdminCenterHA.ps1 -msiPath '.\WindowsAdminCenter.msi' -Verbose
```

### <a name="update-the-certificate-used-by-windows-admin-center"></a>更新 Windows Admin Center 使用的证书

通过提供新的证书 .pfx 文件和密码，可以随时更新 Windows Admin Center 的 HA 部署使用的证书。

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -certPath "cert.pfx" -certPassword $certPassword -Verbose
```

还可以在使用新的 .msi 文件更新 Windows Admin Center 的同时更新证书。

```powershell
$certPassword = Read-Host -AsSecureString
.\Install-WindowsAdminCenterHA.ps1 -msiPath ".\WindowsAdminCenter.msi" -certPath "cert.pfx" -certPassword $certPassword -Verbose
``` 

## <a name="uninstall"></a>卸载

若要从故障转移群集中卸载 Windows Admin Center 的 HA 部署，请将 ```-Uninstall``` 参数传递到 ```Install-WindowsAdminCenterHA.ps1``` 脚本。

```powershell
.\Install-WindowsAdminCenterHA.ps1 -Uninstall -Verbose
```

## <a name="troubleshooting"></a>疑难解答

日志保存在 CSV 的临时文件夹中（例如 C:\ClusterStorage\Volume1\temp）。