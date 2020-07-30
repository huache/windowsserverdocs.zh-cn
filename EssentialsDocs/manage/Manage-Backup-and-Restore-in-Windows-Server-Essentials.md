---
title: 管理 Windows Server Essentials 中的备份和还原
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 41000915-f6ff-4dbb-b7be-629ef36386d4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 2f42cd78bb5cc3198421edccd32c05e2eada7be0
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181033"
---
# <a name="manage-backup-and-restore-in-windows-server-essentials"></a>管理 Windows Server Essentials 中的备份和还原

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

 Windows Server Essentials 提供了可靠的方法来执行你的服务器的常规备份和网络计算机的备份。 发生数据丢失时，你可以从服务器上的成功备份中恢复数据，而无需还原整个计算机。 如有必要，你可以对网络中的服务器或客户端计算机执行完整的系统还原。 下表描述了对你可用的不同备份选项及它们的优点。

|备份功能|描述|优点|
|--------------------|-----------------|----------------|
|服务器备份|备份运行 Windows Server Essentials 的服务器。 将数据备份到外部 USB 驱动器。<br /><br /> 有关详细信息，请参阅[管理服务器备份](Manage-Server-Backup-in-Windows-Server-Essentials.md)和[还原或修复服务器](Restore-or-repair-your-server-running-Windows-Server-Essentials.md)。|-可以还原服务器上的文件和文件夹。<br /><br /> -可以对服务器执行完整的系统还原。|
|Client Computer Backup|备份网络中的客户端计算机。 在运行 Windows Server Essentials 的服务器上备份数据。<br /><br /> 有关详细信息，请参阅[管理客户端备份](Manage-Client-Computer-Backup-in-Windows-Server-Essentials.md)和[从现有的客户端计算机备份还原完整系统](Restore-a-full-system-from-an-existing-client-computer-backup.md)。|-可以从服务器还原文件和文件夹。<br /><br /> -可以对客户端计算机执行完整的系统还原。|
| Microsoft Azure 备份|在服务器上执行文件或文件夹的联机备份。 使用 Azure 备份来备份服务器数据时，将使用你的密码加密信息，然后将其上传到 Internet 上的安全数据中心。<br /><br /> 有关详细信息，请参阅[管理联机备份](Manage-Online-Backup-in-Windows-Server-Essentials.md)。|-可以从服务器还原文件和文件夹。<br /><br /> -对于增量备份，只有对文件进行的更改才会传输到云中。<br /><br /> -备份存储在 Microsoft Azure 中，并处于场外位置，从而减少了保护现场备份媒体的需要。|

## <a name="additional-references"></a>其他参考

-   [管理 Windows Server Essentials](Manage-Windows-Server-Essentials.md)

-   [使用 Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)
