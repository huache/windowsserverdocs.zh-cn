---
title: cleanmgr
description: '配置磁盘清理工具 ( # A0) 自动清理某些文件。'
ms.reviewer: cosmosdarwin
author: iangpgh
ms.author: jgerend
manager: daveba
ms.date: 06/20/2019
ms.openlocfilehash: 81a9283ef75ef76b14a8ee8a5ecc3ab225207560
ms.sourcegitcommit: 0b3d6661c44aa1a697087e644437279142726d84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90083658"
---
# <a name="cleanmgr"></a>cleanmgr

> 适用于： Windows Server 2019，Windows Server 2016，Windows Server 2012，Windows Server 2008 R2，Windows Server (半年通道) 

清除计算机硬盘上不必要的文件。 你可以使用命令行选项来指定 **cleanmgr.exe** 清理临时文件、Internet 文件、下载的文件以及回收站文件。 然后，你可以使用 " **计划任务** " 工具计划在特定时间运行的任务。

## <a name="syntax"></a>语法

```
cleanmgr [/d <driveletter>] [/sageset:n]  [/sagerun:n] [/TUNEUP:n] [/LOWDISK] [/VERYLOWDISK]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /d `<driveletter>` | 指定想要磁盘清理清理的驱动器。<p>**注意：****/D**选项不能与一起使用 `/sagerun:n` 。 |
| /sageset： n | 显示 " **磁盘清理设置** " 对话框，并创建用于存储所选设置的注册表项。 `n`值（存储在注册表中）允许您指定要运行的 "磁盘清理" 任务。 `n`该值可以是0到9999之间的任何整数值。 |
| /sagerun： n | 如果使用 **/sageset** 选项，则运行分配给 n 值的指定任务。 将枚举计算机上的所有驱动器，并针对每个驱动器运行所选配置文件。 |
| /tuneup： n | 为相同的运行 **/sageset** 和 **/sagerun** `n` 。 |
| /lowdisk | 用默认设置运行。 |
| /verylowdisk | 用默认设置运行，不提示用户。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="options"></a>选项

可以通过使用 **/sageset** 和 **/Sagerun** 为磁盘清理指定的文件选项包括：

- **临时安装文件** -这些文件是由不再运行的安装程序所创建的文件。

- **下载的程序文件** -下载的程序文件是 ActiveX 控件和 Java 程序，可在查看某些页面时从 Internet 上自动下载。 这些文件临时存储在硬盘上的 "已下载的 Program Files" 文件夹中。 此选项包括 "查看文件" 按钮，以便您可以在 "磁盘清理" 删除文件之前查看这些文件。 按钮将打开 "C:\Winnt\Downloaded Program Files" 文件夹。

- **Internet 临时文件** -"临时 internet 文件" 文件夹包含存储在您的硬盘上用于快速查看的网页。 "磁盘清理" 将删除这些页面，但不会使网页的个性化设置保持不变。 此选项还包含 "查看文件" 按钮，该按钮可打开 C:\documents and 和 Settings\Username\Local Settings\Temporary Internet Files\Content.IE5 文件夹。

- **旧的 Chkdsk 文件** -chkdsk 检查磁盘错误时，chkdsk 可能会将丢失的文件碎片作为文件保存在磁盘上的根文件夹中。 不需要这些文件。

- **回收站** -回收站包含已从计算机中删除的文件。 在清空回收站之前，不会永久删除这些文件。 此选项包括打开回收站的 "查看文件" 按钮。<p>**注意：** 例如，回收站可能出现在多个驱动器中，而不只是位于% SystemRoot%。

- **临时文件** -程序有时会将临时信息存储在临时文件夹中。 程序退出之前，该程序通常会删除此信息。 您可以安全地删除过去一周内未修改的临时文件。

- **临时脱机文件** -临时脱机文件是最近使用的网络文件的本地副本。 将自动缓存这些文件，以便你可以在断开网络连接后使用这些文件。 " **查看文件** " 按钮将打开脱机文件文件夹。

- **脱机文件** 脱机文件是网络文件的本地副本，你想要使其脱机可用，以便在断开网络连接后可以使用它们。 " **查看文件** " 按钮将打开脱机文件文件夹。

- **压缩旧文件** -Windows 可以压缩最近未使用的文件。 压缩文件可节省磁盘空间，但仍可使用这些文件。 不删除任何文件。 由于文件以不同的速率进行压缩，因此所显示的磁盘空间量将为近似值。 使用 "选项" 按钮，可以指定在 "磁盘清理" 压缩未使用的文件之前要等待的天数。

- **内容索引器的目录文件** -索引服务通过保留磁盘上的文件的索引来提高和提高文件搜索的速度。 这些目录文件保留自上一索引操作，可以安全地删除。<p>**注意：** 目录文件可能出现在多个驱动器中，例如，不只是在中 `%SystemRoot%` 。

>[!NOTE]
> 如果指定清理包含 Windows 安装的驱动器，则所有这些选项都在 " **磁盘清理** " 选项卡上可用。如果指定任何其他驱动器，则 " **磁盘清理** " 选项卡上仅提供 "回收站" 和 "内容索引" 选项的编录文件。

## <a name="examples"></a>示例

若要运行 "磁盘清理" 应用，以便可以使用其对话框指定以后要使用的选项，请将设置保存到集 **1**，键入以下内容：

```
cleanmgr /sageset:1
```

若要运行磁盘清理并包括通过 cleanmgr.exe/sageset：1命令指定的选项，请键入：

```
cleanmgr /sagerun:1
```

若要 `cleanmgr /sageset:1` `cleanmgr /sagerun:1` 一起运行，请键入：

```
cleanmgr /tuneup:1
```

## <a name="additional-references"></a>其他参考

- [在 Windows 10 中释放驱动器空间](https://support.microsoft.com/help/12425/windows-10-free-up-drive-space)

- [命令行语法项](command-line-syntax-key.md)
