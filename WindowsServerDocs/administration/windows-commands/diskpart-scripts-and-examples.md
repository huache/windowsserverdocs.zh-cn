---
title: diskpart 脚本和示例
description: 有关的详细信息，请参阅有关如何自动执行磁盘相关任务（例如创建卷或将磁盘转换为动态磁盘）的示例。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 319c0795-11df-47c8-b203-eadb0577ee0d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 546f867b2cde199f54975a127b0faf11130996d2
ms.sourcegitcommit: 5e313a004663adb54c90962cfdad9ae889246151
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84354667"
---
# <a name="diskpart-scripts-and-examples"></a>diskpart 脚本和示例

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

用于 `diskpart /s` 运行自动执行与磁盘相关的任务的脚本，例如创建卷或将磁盘转换为动态磁盘。 如果是使用无人参与安装或 Sysprep（它们不支持创建除启动卷以外的卷）部署 Windows，则创建执行这些任务的脚本非常有用。

若要创建一个 diskpart 脚本，请创建一个包含要运行的 Diskpart 命令的文本文件，其中每行一个命令，而不是空行。 您可以通过开始一行， `rem` 使该行成为注释。 例如，以下脚本将擦除磁盘，然后为 Windows 恢复环境创建 300 MB 的分区：

    ```
    select disk 0
    clean
    convert gpt
    create partition primary size=300
    format quick fs=ntfs label=Windows RE tools
    assign letter=T
    ```

## <a name="examples"></a>示例

- 若要运行 diskpart 脚本，请在命令提示符下键入以下命令，其中*scriptname*是包含你的脚本的文本文件的名称：

    ```
    diskpart /s scriptname.txt
    ```

- 若要将 diskpart 的脚本输出重定向到文件，请键入以下命令，其中*logfile*是 diskpart 写入其输出的文本文件的名称：

    ```
    diskpart /s scriptname.txt > logfile.txt
    ```

### <a name="remarks"></a>备注

- 将**diskpart**命令用作脚本的一部分时，建议你将所有 diskpart 操作一起作为一个 diskpart 脚本的一部分来完成。 您可以运行连续的 diskpart 脚本，但必须在每个脚本之间至少使用15秒，才能完全关闭以前的执行，然后在后续脚本中再次运行**diskpart**命令。 否则，连续脚本可能会运行失败。 可以通过将命令添加到批处理文件中，并将其添加 `timeout /t 15` 到你的 diskpart 脚本，在连续的 diskpart 脚本之间添加暂停。

- 启动 diskpart 时，diskpart 版本和计算机名称将显示在命令提示符下。 默认情况下，如果在尝试执行脚本任务时，diskpart 遇到错误，则 diskpart 将停止处理脚本并显示错误代码（除非已指定**noerr**参数）。 但是，无论使用的是**noerr**参数，diskpart 始终会在遇到语法错误时返回错误。 通过**noerr**参数，你可以执行一些有用的任务，例如，使用单个脚本删除所有磁盘上的所有分区，而不考虑磁盘的总数量。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [示例：使用 Windows PE 和 DiskPart 配置基于 UEFI/GPT 的硬盘驱动器分区](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-8.1-and-8/hh825686(v=win.10))

- [示例：使用 Windows PE 和 DiskPart 配置基于 BIOS/MBR 的硬盘分区](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-8.1-and-8/hh825677(v=win.10))

- [Windows PowerShell 中的存储 Cmdlet](https://docs.microsoft.com/powershell/module/storage/?view=win10-ps)
