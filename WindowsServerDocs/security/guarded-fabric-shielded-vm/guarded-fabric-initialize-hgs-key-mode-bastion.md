---
title: 使用堡垒林中的密钥模式初始化 HGS 群集
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: b526895f9b9e819523ee459701c2f09988565544
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87965994"
---
# <a name="initialize-the-hgs-cluster-using-key-mode-in-an-existing-bastion-forest"></a>使用现有堡垒林中的密钥模式初始化 HGS 群集

> 适用于：Windows Server 2019
>
> [!div class="step-by-step"]
> [«在新林中](guarded-fabric-install-hgs-in-a-bastion-forest.md) 
>  安装 HGS[创建主机密钥»](guarded-fabric-create-host-key.md)

Active Directory 域服务将安装在计算机上，但应保留未配置。

[!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)]

继续之前，请确保已为主机保护者服务预留群集对象，并授予已登录的用户对 Active Directory 中的 VCO 和 CNO 对象的**完全控制**权限。
需要将虚拟计算机对象名称传递给 `-HgsServiceName` 参数，并将群集名称传递给 `-ClusterName` 参数。

> [!TIP]
> 请仔细检查 AD 域控制器，确保群集对象已复制到所有 Dc，然后再继续。

如果使用的是基于 PFX 的证书，请在 HGS 服务器上运行以下命令：

```powershell
$signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
$encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

Install-ADServiceAccount -Identity 'HGSgMSA'

Initialize-HgsServer -UseExistingDomain -ServiceAccount 'HGSgMSA' -JeaReviewersGroup 'HgsJeaReviewers' -JeaAdministratorsGroup 'HgsJeaAdmins' -HgsServiceName 'HgsService' -ClusterName 'HgsCluster' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustHostKey
```

如果使用本地计算机上安装的证书 (例如 HSM 支持的证书和不可导出的证书) ，请 `-SigningCertificateThumbprint` `-EncryptionCertificateThumbprint` 改用和参数。

