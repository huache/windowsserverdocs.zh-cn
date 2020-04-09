---
title: 在新林中安装 HGS
ms.prod: windows-server
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 8f896b0cea49f9dd26a828a2580b59a78348763a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80856600"
---
# <a name="install-hgs-in-a-new-forest"></a>在新林中安装 HGS 

>适用于： Windows Server 2019、Windows Server （半年频道）、Windows Server 2016

## <a name="add-the-hgs-server-role"></a>添加 HGS 服务器角色

在已提升权限的 PowerShell 会话中运行以下命令，以添加 HGS 服务器角色并安装 HGS。

[!INCLUDE [Install the HGS server role](../../../includes/guarded-fabric-install-hgs-server-role.md)] 

## <a name="install-hgs"></a>安装 HGS 

[!INCLUDE [Install HGS by default](../../../includes/install-hgs-default.md)] 

## <a name="next-steps"></a>后续步骤

- 有关设置基于 TPM 的证明的后续步骤，请参阅[在新的专用林中使用 TPM 模式初始化 HGS 群集（默认值）](guarded-fabric-initialize-hgs-tpm-mode-default.md)。
- 有关设置主机密钥证明的后续步骤，请参阅[在新的专用林中使用密钥模式初始化 HGS 群集（默认值）](guarded-fabric-initialize-hgs-key-mode-default.md)。
- 有关设置基于管理员的证明的后续步骤（在 Windows Server 2019 中不推荐使用），请参阅[在新的专用林中使用 AD 模式初始化 HGS 群集（默认值）](guarded-fabric-initialize-hgs-ad-mode-default.md)。

## <a name="next-step"></a>下一步

> [!div class="nextstepaction"]
> [初始化 HGS](guarded-fabric-initialize-hgs.md)


