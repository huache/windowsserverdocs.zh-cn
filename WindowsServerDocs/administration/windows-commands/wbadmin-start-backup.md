---
title: wbadmin start backup
description: 使用指定参数创建备份的 wbadmin 开始备份参考文章。
ms.topic: reference
ms.assetid: 56f3e752-d99a-4c3d-8e97-10303c37dd78
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: cc59c24e84d7dd5eb4455df656ee1bb3193c6af5
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640269"
---
# <a name="wbadmin-start-backup"></a>wbadmin start backup

使用指定参数创建备份。 如果未指定任何参数，并且已创建计划的每日备份，则此子命令将使用计划备份的设置来创建备份。 如果指定了参数，它将创建一个卷影复制服务 (VSS) 复制备份，并且不会更新正在备份的文件的历史记录。

若要使用此子命令创建一次性备份，您必须是 **Backup Operators** 组或 **Administrators** 组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行 **wbadmin** 。  (打开提升的命令提示符，右键单击 " **命令提示符** "，然后单击 "以 **管理员身份运行**"。 ) 

## <a name="syntax"></a>语法

Windows Vista 和 Windows Server 2008 的语法：
```
wbadmin start backup
[-backupTarget:{<BackupTargetLocation> | <TargetNetworkShare>}]
[-include:<VolumesToInclude>]
[-allCritical]
[-noVerify]
[-user:<UserName>]
[-password:<Password>]
[-noinheritAcl]
[-vssFull]
[-quiet]
```
Windows 7 和 Windows Server 2008 R2 及更高版本的语法：
```
Wbadmin start backup
[-backupTarget:{<BackupTargetLocation> | <TargetNetworkShare>}]
[-include:<ItemsToInclude>]
[-nonRecurseInclude:<ItemsToInclude>]
[-exclude:<ItemsToExclude>]
[-nonRecurseExclude:<ItemsToExclude>]
[-allCritical]
[-systemState]
[-noVerify]
[-user:<UserName>]
[-password:<Password>]
[-noInheritAcl]
[-vssFull | -vssCopy]
[-quiet]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|-backupTarget|指定此备份的存储位置。 要求使用硬盘驱动器号 (f： ) ，其格式为基于卷 GUID 的路径 \\ \\ ？ \\卷 {GUID} 或通用命名约定 (到远程共享文件夹的 UNC) 路径 (\\ \\ \<servername> \\ \<sharename> \\) 。 默认情况下，备份将保存在： \\ \\ \<servername> \\ \<sharename> \\ **WindowsImageBackup** \\ \<ComputerBackedUp> \\ 。</br>重要提示：如果将备份保存到远程共享文件夹，则在使用同一文件夹再次备份同一台计算机时，将覆盖该备份。 另外，如果备份操作失败，则最终可能得不到任何备份，这是因为原有备份已被覆盖，而新备份却不可用。 可以通过在远程共享文件夹中创建子文件夹来组织您的备份，避免出现这种情况。 如果这样做，则子文件夹将需要父文件夹的两倍空间。|
|-include|对于 Windows Vista 和 Windows Server 2008，指定要包含在备份中的卷驱动器号、卷装入点或基于 GUID 的卷名的逗号分隔列表。 仅当使用 **-backupTarget** 参数时，才应使用此参数。</br>对于 Windows 7 和 Windows Server 2008 R2 及更高版本，指定要包含在备份中的项的逗号分隔列表。 可以包含多个文件、文件夹或卷。 可以使用卷驱动器号、卷装入点或基于 GUID 的卷名称指定卷路径。 如果使用基于 GUID 的卷名，则应使用反斜杠 () 来终止它 \\ 。 指定文件路径时，可以使用通配符 (文件名 \*) 。 仅当使用 **-backupTarget** 参数时才应使用。|
|-exclude|对于 Windows 7 和 Windows Server 2008 R2 及更高版本，指定要从备份中排除的以逗号分隔的项列表。 可以排除文件、文件夹或卷。 可以使用卷驱动器号、卷装入点或基于 GUID 的卷名称指定卷路径。 如果使用基于 GUID 的卷名，则应使用反斜杠 () 来终止它 \\ 。 指定文件路径时，可以使用通配符 (文件名 \*) 。 仅当使用 **-backupTarget** 参数时才应使用。|
|-nonRecurseInclude|对于 Windows 7 和 Windows Server 2008 R2 及更高版本，指定要包含在备份中的非递归、以逗号分隔的项列表。 可以包含多个文件、文件夹或卷。 可以使用卷驱动器号、卷装入点或基于 GUID 的卷名称指定卷路径。 如果使用基于 GUID 的卷名，则应使用反斜杠 () 来终止它 \\ 。 指定文件路径时，可以使用通配符 (文件名 \*) 。 仅当使用 **-backupTarget** 参数时才应使用。|
|-nonRecurseExclude|对于 Windows 7 和 Windows Server 2008 R2 及更高版本，指定要从备份中排除的非递归、以逗号分隔的项列表。 可以排除文件、文件夹或卷。 可以使用卷驱动器号、卷装入点或基于 GUID 的卷名称指定卷路径。 如果使用基于 GUID 的卷名，则应使用反斜杠 () 来终止它 \\ 。 指定文件路径时，可以使用通配符 (文件名 \*) 。 仅当使用 **-backupTarget** 参数时才应使用。|
|-allCritical|指定包含操作系统状态 (卷) 包含在备份中的所有关键卷。 如果要为裸机恢复创建备份，此参数非常有用。 仅当指定了 **-backupTarget** 时才应使用它，否则命令将失败。 可以与 **-include** 选项一起使用。</br>提示：关键卷备份的目标卷可以是本地驱动器，但不能是备份中包含的任何卷。|
|-systemState|对于 Windows 7 和 Windows Server 2008 R2 及更高版本，将创建一个包含系统状态的备份以及使用 **-include** 参数指定的任何其他项。 系统状态包含启动文件 ( # A0、NDTLDR、NTDetect.com) 、Windows 注册表（包括 COM 设置、SYSVOL (组策略和登录脚本) 、Active Directory 和 NTDS）。域控制器上的 DIT 以及证书服务（如果安装了证书服务）。 如果服务器已安装 Web 服务器角色，则将包括 IIS 元目录。 如果该服务器是群集的一部分，则还会包括群集服务信息。|
|-noVerify|指定将备份保存到可移动媒体 (例如，不验证 DVD) 是否有错误。 如果不使用此参数，则会验证保存到可移动媒体的备份是否存在错误。|
|-user|如果将备份保存到远程共享文件夹，请指定对文件夹具有写入权限的用户名。|
|-password|指定参数 **-user**提供的用户名的密码。|
|-noInheritAcl|将 (ACL) 权限的访问控制列表与 **-user**和 **-password**参数提供的凭据对应 \\ \\ \<servername> \\ \<sharename> \\ \\ \<ComputerBackedUp> \\ (包含备份) 的文件夹。 若要稍后访问备份，则必须使用这些凭据，或者必须是使用共享文件夹的计算机上的 Administrators 组或 Backup Operators 组的成员。 如果未使用 **-noInheritAcl** ，则默认情况下会将远程共享文件夹的 ACL 权限应用到 \\ \<ComputerBackedUp> 文件夹，以便能够访问远程共享文件夹的任何人均可访问备份。|
|-vssFull|使用卷影复制服务 (VSS) 执行完整备份。 所有文件均已备份，每个文件的历史记录都会更新以反映它已备份，并且以前的备份的日志可能会被截断。 如果未使用此参数，则 **wbadmin start backup** 会进行复制备份，但不会更新正在备份的文件的历史记录。</br>警告：如果你使用的产品不是 Windows Server 备份来备份当前备份中包含的卷上的应用程序，请勿使用此参数。 这样做可能会破坏其他备份产品所创建的增量备份、差异备份或其他类型的备份，因为他们要依赖的历史记录确定要备份的数据量，并且可能不必要地执行完整备份。|
|-vssCopy|对于 Windows 7 和 Windows Server 2008 R2 及更高版本，使用 VSS 执行副本备份。 所有文件都已备份，但不会更新正在备份的文件的历史记录，因此，你可以保留更改、删除等文件的所有信息以及任何应用程序日志文件。 使用这种类型的备份不会影响独立于此副本备份而发生的增量备份和差异备份的序列。 这是默认值。</br>警告：不能将副本备份用于增量备份或差异备份或还原。|
|-quiet|对用户运行无提示的子命令。|

## <a name="examples"></a>示例

下面的示例演示如何在不同的备份方案中使用 **wbadmin start backup** 命令：

方案 #1
- 创建卷 e：、d： \\ 装入点和 \\ \\ ？ \\卷 {cc566d14-4410-11d9-9d93-806e6f6e6963}
- 将备份保存到卷 f：
  ```
  wbadmin start backup -backupTarget:f: -include:e:,d:\mountpoint,\\?\Volume{cc566d14-44a0-11d9-9d93-806e6f6e6963}\
  ```
  方案 #2
- 执行 *f： \\ folder1* 和 *h： \\ folder2* 到卷 *d：* 的一次性备份。
- 备份系统状态
- 进行复制备份，以便不影响正常计划的差异备份。
  ```
  wbadmin start backup –backupTarget:d: -include:g\folder1,h:\folder2 –systemstate -vsscopy
  ```
  方案 #3
- 对应以非递归方式备份的 *d： \\ folder1* 执行一次性备份。
- 将文件夹备份到网络位置* \\ \\ backupshare \\ 备份 1*
- 限制对 **Administrators** 组或 **backup Operators** 组成员的备份访问。
  ```
  wbadmin start backup –backupTarget: \\backupshare\backup1 -noinheritacl -nonrecurseinclude:d:\folder1
  ```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
