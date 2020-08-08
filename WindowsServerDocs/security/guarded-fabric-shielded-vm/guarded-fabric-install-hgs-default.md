---
title: 在新林中安装 HGS
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: c18c14435c93d08c98b1a765fd820294a273a575
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939541"
---
# <a name="install-hgs-in-a-new-forest"></a>在新林中安装 HGS

>适用于： Windows Server 2019、Windows Server (半年频道) 、Windows Server 2016

## <a name="add-the-hgs-server-role"></a>添加 HGS 服务器角色

在已提升权限的 PowerShell 会话中运行以下命令，以添加 HGS 服务器角色并安装 HGS。

[!INCLUDE [Install the HGS server role](../../../includes/guarded-fabric-install-hgs-server-role.md)]

## <a name="install-hgs"></a>安装 HGS

[!INCLUDE [Install HGS by default](../../../includes/install-hgs-default.md)]

## <a name="next-steps"></a>后续步骤

- 有关设置基于 TPM 的证明的后续步骤，请参阅[在新的专用林中使用 TPM 模式初始化 HGS 群集 (默认) ](guarded-fabric-initialize-hgs-tpm-mode-default.md)。
- 有关设置主机密钥证明的后续步骤，请参阅[在新的专用林中使用密钥模式初始化 HGS 群集 (默认) ](guarded-fabric-initialize-hgs-key-mode-default.md)。
- 若要在 Windows Server 2019) 中 (弃用的后续步骤，请参阅在[新的专用林中使用 AD 模式初始化 HGS 群集 (默认) ](guarded-fabric-initialize-hgs-ad-mode-default.md)。

## <a name="next-step"></a>后续步骤

> [!div class="nextstepaction"]
> [初始化 HGS](guarded-fabric-initialize-hgs.md)


