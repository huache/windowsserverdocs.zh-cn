---
title: SMB 安全增强功能
description: Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2016 中的 SMB 加密功能的说明。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 07/09/2018
ms.localizationpriority: medium
ms.openlocfilehash: 9052e9e6a1327b67fd75b07ab2ee6fc56b1190ac
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86962130"
---
# <a name="smb-security-enhancements"></a>SMB 安全增强功能

>适用于：Windows Server 2012 R2、Windows Server 2012、Windows Server 2016

本主题介绍 Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2016 中的 SMB 安全增强功能。

## <a name="smb-encryption"></a>SMB 加密

SMB 加密提供 SMB 数据的端对端加密，并防止数据在未受信任网络中遭到窃听。 你可以通过最少的工作量来部署 SMB 加密，但对于专用硬件或软件，可能需要少量额外成本。 它对 Internet 协议安全性 (IPsec) 或 WAN 加速器无要求。 SMB 加密可针对每次共享配置，也可以针对整个文件服务器配置，并且可以在数据通过不受信任的网络的各种场景中启用。

>[!NOTE]
>SMB 加密不涉及静态安全性，这通常由 BitLocker 驱动器加密处理。

如果需要保护敏感数据免受中间人攻击，应考虑进行 SMB 加密。 可能的方案包括：

- 使用 SMB 协议移动信息工作者的敏感数据。 SMB 加密在文件服务器和客户端之间提供端到端的隐私和完整性保障，无需考虑传输数据的网络，例如由非 Microsoft 提供商维护的广域网 (WAN) 连接。
- 借助 SMB 3.0，文件服务器可为服务器应用程序（如 SQL Server 或 Hyper-V）提供持续可用的存储。 启用 SMB 加密可提供保护信息免受窥探攻击的机会。 SMB 加密比大多数存储区域网络 (SAN) 所需的专用硬件解决方案更容易使用。

>[!IMPORTANT]
>请注意，与不加密相比，任何端到端的加密保护都会产生显著的性能操作成本。

## <a name="enable-smb-encryption"></a>启用 SMB 加密

你可以为整个文件服务器启用 SMB 加密，也可以只为特定文件共享启用 SMB 加密。 可以使用以下方法之一来启用 SMB 加密:

### <a name="enable-smb-encryption-with-windows-powershell"></a>使用 Windows PowerShell 启用 SMB 加密

1. 若要为单个文件共享启用 SMB 加密，请在服务器上键入以下脚本：
    
    ```PowerShell
    Set-SmbShare –Name <sharename> -EncryptData $true
    ```
2. 若要为整个文件服务器启用 SMB 加密，请在服务器上键入以下脚本：
    
    ```PowerShell
    Set-SmbServerConfiguration –EncryptData $true
    ```
3. 若要创建新的 SMB 文件共享并启用 SMB 加密，请键入以下脚本：
    
    ```PowerShell
    New-SmbShare –Name <sharename> -Path <pathname> –EncryptData $true
    ```

### <a name="enable-smb-encryption-with-server-manager"></a>使用服务器管理器启用 SMB 加密

1. 在“服务器管理器”中，打开“文件和存储服务”  。
2. 选择“共享”以打开“共享”管理页  。
3. 右键单击要启用 SMB 加密的共享，然后选择“属性”  。
4. 在共享的“设置”页上，选择“加密数据访问”   。 对此共享的远程文件访问已加密。

### <a name="considerations-for-deploying-smb-encryption"></a>部署 SMB 加密的注意事项

默认情况下，为文件共享或服务器启用 SMB 加密时，只允许 SMB 3.0 客户端访问指定的文件共享。 这会加强管理员为访问共享的所有客户端数据提供保护的意识。 但是，在某些情况下，管理员可能想要允许对不支持 SMB 3.0 的客户端（例如，在使用混合客户端操作系统版本的过渡期间）进行未加密访问。 若要允许对不支持 SMB 3.0 的客户端进行未加密访问，请在 Windows PowerShell 中键入以下脚本：

```PowerShell
Set-SmbServerConfiguration –RejectUnencryptedAccess $false
```

下一节中所述的安全方言协商功能可防止中间人攻击从 SMB 3.0 降级到 SMB 2.0 的连接（这将使用未加密的访问）。 但是，它不会阻止降级到 SMB 1.0，这也会导致未加密的访问。 为了保证 SMB 3.0 客户端始终使用 SMB 加密来访问已加密共享，必须禁用 SMB 1.0 服务器。 （有关说明，请参阅[禁用 SMB 1.0](#disabling-smb-10) 部分。）如果“–RejectUnencryptedAccess”设置保留为其默认设置“$true”，则仅允许支持加密的 SMB 3.0 客户端访问文件共享（SMB 1.0 客户端也会被拒绝）   。

>[!NOTE]
>* SMB 加密使用高级加密标准 (AES)-CCM 算法加密和解密数据。 无论 SMB 签名设置如何，AES-CCM 还能为加密的文件共享提供数据完整性验证（签名）。 如果要在不加密的情况下启用 SMB 签名，则可继续执行此操作。 有关详细信息，请参阅 [SMB 签名的基础知识](/archive/blogs/josebda/the-basics-of-smb-signing-covering-both-smb1-and-smb2)。
>* 如果你的组织使用广域网 (WAN) 加速设备，则当你尝试访问文件共享或服务器时，可能会遇到问题。
>* 使用默认配置（其中没有允许对已加密文件共享进行未加密访问）时，如果不支持 SMB 3.0 的客户端尝试访问已加密文件共享，则事件 ID 1003 会记录到 Microsoft-Windows-SmbServer/Operational 事件日志中，并且客户端将收到一条“拒绝访问”的错误消息  。
>* SMB 加密与 NTFS 文件系统中的加密文件系统 (EFS) 无关，并且 SMB 加密不需要或依赖于使用 EFS。
>* SMB 加密与 BitLocker 驱动器加密无关，并且SMB 加密不需要或依赖于使用 BitLocker 驱动器加密。

## <a name="secure-dialect-negotiation"></a>安全方言协商

SMB 3.0 能够检测到中间人攻击，这些攻击会尝试对 SMB 2.0 或 SMB 3.0 协议，或者客户端与服务器协商的功能进行降级。 当客户端或服务器检测到这种攻击时，会断开连接，并在 Microsoft-Windows-SmbServer/Operational 事件日志中记录事件 ID 1005。 安全方言协商无法检测或阻止从 SMB 2.0 或3.0 降级到 SMB 1.0。 因此，为了充分利用 SMB 加密的完整功能，我们强烈建议你禁用 SMB 1.0 服务器。 有关详细信息，请参阅[禁用 SMB 1.0](#disabling-smb-10)。

下一节中所述的安全方言协商功能可防止中间人攻击从 SMB 3 降级到 SMB 2 的连接（这将使用未加密的访问）；但是，它不会阻止降级到 SMB 1，这也会导致未加密的访问。 有关 SMB 早期非 Windows 实现的潜在问题的详细信息，请参阅 [Microsoft 知识库](https://support.microsoft.com/kb/2686098)。

## <a name="new-signing-algorithm"></a>新签名算法

SMB 3.0 使用较新的加密算法进行签名：基于高级加密标准 (AES) 密码的消息身份验证代码 (CMAC)。 SMB 2.0 使用较旧的 HMAC-SHA256 加密算法。 AES-CMAC 和 AES-CCM 可以显著地加快大多数支持 AES 指令的新式 CPU 上的数据加密。 有关详细信息，请参阅 [SMB 签名的基础知识](/archive/blogs/josebda/the-basics-of-smb-signing-covering-both-smb1-and-smb2)。

## <a name="disabling-smb-10"></a>禁用 SMB 1.0

SMB 1.0 中的传统计算机浏览器服务和远程管理协议功能是独立的，并且可以去除。 系统仍会默认启用这些功能，但如果你没有早期的 SMB 客户端（例如运行 Windows Server 2003 或 Windows XP 的计算机），则可以删除 SMB 1.0 功能以提高安全性，并可以减少需要修补的情况。

>[!NOTE]
>SMB 2.0 是在 Windows Server 2008 和 Windows Vista 中引入的。 早期客户端（例如运行 Windows Server 2003 或 Windows XP 的计算机）不支持 SMB 2.0；因此，如果禁用 SMB 1.0 服务器，它们将无法访问文件共享或打印共享。 此外，某些非 Microsoft SMB 客户端可能无法访问 SMB 2.0 文件共享或打印共享（例如，具有“扫描以共享”功能的打印机）。

开始禁用 SMB 1.0 之前，你需要了解你的 SMB 客户端当前是否连接到运行 SMB 1.0 的服务器。 为此，请在 Windows PowerShell 中输入以下 cmdlet：

```PowerShell
Get-SmbSession | Select Dialect,ClientComputerName,ClientUserName | ? Dialect -lt 2
```

>[!NOTE]
>你应在一周内（每天多次）重复运行此脚本，以生成审核线索。 你还可以将其作为计划任务运行。

若要禁用 SMB 1.0，请在 Windows PowerShell 中输入以下脚本：

```PowerShell
Set-SmbServerConfiguration –EnableSMB1Protocol $false
```

>[!NOTE]
>如果因禁用了运行 SMB 1.0 的服务器而导致 SMB 客户端连接被拒绝，Microsoft-Windows-SmbServer/Operational 事件日志中会记录事件 ID 1001。

## <a name="more-information"></a>详细信息

下面是一些关于 SMB 和 Windows Server 2012 中相关技术的附加资源。

- [服务器消息块](file-server-smb-overview.md)
- [Windows Server 中的存储](../storage.yml)
- [应用程序数据横向扩展文件服务器](../../failover-clustering/sofs-overview.md)
