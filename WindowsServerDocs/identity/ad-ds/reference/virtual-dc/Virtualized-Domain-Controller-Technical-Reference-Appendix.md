---
ms.assetid: 73a4deba-7da6-4eae-8fdd-2a4d369f9cbb
title: 虚拟化域控制器技术参考附录
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 6387abbe150630d2fd8f6f14724618a6ab32b94a
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88940277"
---
# <a name="virtualized-domain-controller-technical-reference-appendix"></a>虚拟化域控制器技术参考附录

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

本主题的内容：

-   [术语](../../../ad-ds/reference/virtual-dc/../../../ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Technical-Reference-Appendix.md#BKMK_Terms)

-   [FixVDCPermissions.ps1](../../../ad-ds/reference/virtual-dc/../../../ad-ds/reference/virtual-dc/Virtualized-Domain-Controller-Technical-Reference-Appendix.md#BKMK_FixPDCPerms)

## <a name="terminology"></a><a name="BKMK_Terms"></a>术语

-   **Snapshot** -虚拟机在特定时间点的状态。 它依赖于以前拍摄的快照、硬件上和虚拟化平台上的快照链。

-   **Clone** -虚拟机的完整且独立的副本。 它依赖于虚拟硬件)  (虚拟机监控程序。

-   **完全克隆** -完整克隆是虚拟机的独立副本，在克隆操作后与父虚拟机共享任何资源。 完全克隆的正在进行的操作完全独立于父虚拟机。

-   **差异磁盘** -虚拟机的副本，该副本与父虚拟机共享虚拟磁盘。 这通常会节省磁盘空间，并允许多个虚拟机使用相同的软件安装。

-   **VM 副本**-虚拟机的所有相关文件和文件夹的文件系统副本。

-   **Vhd 文件复制** -虚拟机 VHD 的副本

-   **VM 生成 ID** -虚拟机监控程序为虚拟机提供的128位整数。 此 ID 存储在内存中，并在每次应用快照时重置。 该设计使用与虚拟机监控程序无关的机制，在虚拟机中呈现 VM 生成 ID。 Hyper-v 实现在虚拟机的 ACPI 表中公开 ID。

-   **导入/导出** -一项 hyper-v 功能，该功能允许用户将整个虚拟机 (VM 文件、VHD 和计算机配置) 。 然后，它允许用户使用该文件集将计算机恢复到同一 VM 上的同一虚拟机上， (Restore) 、同一 VM (移动) 或新 VM (复制) 

## <a name="fixvdcpermissionsps1"></a><a name="BKMK_FixPDCPerms"></a>FixVDCPermissions.ps1

```
# Unsigned script, requires use of set-executionpolicy remotesigned -force
# You must run the Windows PowerShell console as an elevated administrator

# Load Active Directory Windows PowerShell Module and switch to AD DS drive
import-module activedirectory
cd ad:

## Get Domain NC
$domainNC = get-addomain

## Get groups and obtain their SIDs
$dcgroup = get-adgroup "Cloneable Domain Controllers"

$sid1 = (get-adgroup $dcgroup).sid

## Get the DACL of the domain
$acl = get-acl $domainNC

## The following object specific ACE grants extended right 'Allow a DC to create a clone of itself' for the CDC group to the Domain NC
## 3e0f7e18-2c7a-4c10-ba82-4d926db99a3e is the schemaIDGuid for 'DS-Clone-Domain-Controller"

$objectguid = new-object Guid 3e0f7e18-2c7a-4c10-ba82-4d926db99a3e
$ace1 = new-object System.DirectoryServices.ActiveDirectoryAccessRule $sid1,"ExtendedRight","Allow",$objectguid

## Add the ACE in the ACL and set the ACL on the object

$acl.AddAccessRule($ace1)
set-acl -aclobject $acl $domainNC
write-host "Done writing new VDC permissions."
cd c:
```



