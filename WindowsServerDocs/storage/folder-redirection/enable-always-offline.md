---
title: 启用始终脱机模式以更快地访问文件
description: 如何使用脱机文件的始终脱机模式，以便更快地访问缓存文件和重定向文件夹。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 09/10/2018
ms.localizationpriority: medium
ms.openlocfilehash: 389fdd26a7e1d9824f1eaf0136a544547f08eb05
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "71401956"
---
# <a name="enable-always-offline-mode-for-faster-access-to-files"></a>启用始终脱机模式以更快地访问文件

>适用于：Windows 10、Windows 8、Windows 8.1、Windows Server 2019、Windows Server 2016、Windows Server 2012、Windows Server 2012 R2 和 Windows（半年频道）

本文介绍如何使用脱机文件的始终脱机模式，以便更快地访问缓存文件和重定向文件夹。 始终脱机还可以降低带宽使用量，因为即使用户通过高速网络连接进行连接，他们也始终脱机工作。

## <a name="prerequisites"></a>必备条件

要启用始终脱机模式，环境必须满足以下先决条件。

- 具有一个 Active Directory 域服务 (AD DS) 域且客户端计算机已加入该域。 没有林或域功能级别要求或架构要求。
- 具有运行 Windows 10、Windows 8.1、Windows 8、Windows Server 2016、Windows Server 2012 R2 或 Windows Server 2012 的客户端计算机。 （运行更早版本 Windows 的客户端计算机可能会在遇到非常高速的网络连接时继续切换为联机模式。）
- 安装了组策略管理的计算机。

## <a name="enable-always-offline-mode"></a>启用始终脱机模式

若要启用始终脱机模式，请使用组策略启用“配置慢速链接模式”策略设置，并将延迟设置为 1（毫秒）   。 这样做会导致运行 Windows 8 或 Windows Server 2012 的客户端计算机自动使用始终脱机模式。

>[!NOTE]
>如果网络连接的延迟低于 1 毫秒，运行 Windows 7、Windows Vista、Windows Server 2008 R2 或 Windows Server 2008 的计算机可能会继续切换为联机模式。

1. 打开“组策略管理”  。
2. 若要选择性地为“脱机文件”设置创建新的组策略对象 (GPO)，请右键单击相应的域或组织单位 (OU)，然后选择“在此域中创建 GPO 并在此处创建相关链接”  。
3. 在控制台树中，右键单击要为其配置脱机文件设置的 GPO，然后选择“编辑”  。 此时会显示“组策略管理编辑器”  。
4. 在控制台树的“计算机配置”下，依次展开“策略”、“管理模板”、“网络”和“脱机文件”      。
5. 右键单击“配置慢速链接模式”，然后选择“编辑”   。 系统将显示“配置慢速链接模式”窗口  。
6. 选择“已启用”  。
7. 在“选项”框中，选择“显示”   。 系统将显示“显示内容”窗口  。
8. 在“值名称”框中，指定要为其启用始终脱机模式的文件共享  。
9. 若要在所有文件共享上启用始终脱机模式，请输入 \*  。
10. 在“值”框中，输入“Latency=1”，将延迟阈值设置为 1 毫秒，然后选择“确定”    。

>[!NOTE]
>默认情况下，在始终脱机模式下，Windows 每两小时会在后台同步一次脱机文件缓存中的文件。 若要更改此值，请使用“配置后台同步”策略设置  。

## <a name="more-information"></a>详细信息

* [文件夹重定向、脱机文件和漫游用户策略文件概述](folder-redirection-rup-overview.md)
* [部署文件夹重定向和脱机文件](deploy-folder-redirection.md)