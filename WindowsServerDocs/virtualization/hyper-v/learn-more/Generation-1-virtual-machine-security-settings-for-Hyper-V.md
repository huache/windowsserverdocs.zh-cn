---
title: Hyper-V 的第 1 代虚拟机安全设置
description: 介绍 Hyper-V 管理器中可用于第 1 代虚拟机的安全设置
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8f8c569-8b74-4c19-876e-1c7d00cce308
author: larsiwer
ms.author: kathydav
ms.date: 10/04/2016
ms.openlocfilehash: ceb3c2628546815f9b0af35946e173f4276130d2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392787"
---
# <a name="generation-1-virtual-machine-security-settings"></a>第 1 代虚拟机安全设置

>适用于：Windows Server 2016、Microsoft Hyper-V Server 2016、Windows Server 2019、Microsoft Hyper-V Server 2019

使用 Hyper-V 管理器中的第 1 代虚拟机安全设置来帮助保护虚拟机的数据和状态。

## <a name="encryption-support-settings-in-hyper-v-manager"></a>Hyper-V 管理器中的加密支持设置

可以通过选择以下加密支持选项来帮助保护虚拟机的数据和状态。

- 加密状态和虚拟机迁移流量 - 对虚拟机写入磁盘时的保存状态和实时迁移流量进行加密  。

若要启用此选项，必须为虚拟机添加密钥存储驱动器。

## <a name="key-storage-drive-in-hyper-v-manager"></a>Hyper-V 管理器中的密钥存储驱动器

密钥存储驱动器为虚拟机提供了一个小型驱动器，用于存储 BitLocker 密钥。 这使虚拟机可以对其操作系统磁盘进行加密，而无需虚拟化的受信任的平台模块 (TPM) 芯片。 密钥存储驱动器的内容使用密钥保护程序进行加密。 密钥保护程序授权 Hyper-V 主机运行虚拟机。 密钥存储驱动器和密钥保护程序的内容都作为虚拟机的运行时状态的一部分进行存储。

要解密密钥存储驱动器的内容并启动虚拟机，Hyper-V 主机必须为以下之一：

- 该虚拟机的经授权的受保护结构的一部分，或
- 拥有一个虚拟机保护者的私钥。

若要了解有关受保护的结构的详细信息，请参阅[安全和保障](../../../security/Security-and-Assurance.md)中的受防护的 VM 简介部分。

可以将密钥存储驱动器添加到虚拟机的某个 IDE 控制器上的空槽中。 要执行此操作，请单击“添加密钥存储驱动器”，将密钥存储驱动器添加到此虚拟机的第一个可用 IDE 控制器槽中  。

## <a name="see-also"></a>另请参阅

- [Hyper-V 管理器中的第 2 代虚拟机安全设置](Generation-2-virtual-machine-security-settings-for-hyper-v.md)
- [安全和保障](../../../security/Security-and-Assurance.md)