---
title: format
description: Format 命令的参考文章，其中格式化磁盘来接受 Windows 文件。
manager: dongill
ms.author: jgerend
ms.topic: article
ms.assetid: 51ec7423-9a01-4219-868a-25d69cdcc832
author: jasongerend
ms.date: 10/16/2017
ms.openlocfilehash: a923706252e6094cf12dcdf2632366ee7b2401f8
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87890126"
---
# <a name="format"></a>格式

> 适用于： Windows 10、Windows Server 2016

格式化磁盘以接受 Windows 文件。 您必须是 Administrators 组的成员才能格式化硬盘驱动器。

> [!NOTE]
> 你还可以在恢复控制台中使用带有不同参数的**format**命令。 有关恢复控制台的详细信息，请参阅 windows [RE)  (Windows 恢复环境](/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)。

## <a name="syntax"></a>语法

```
format <volume> [/fs:{FAT|FAT32|NTFS}] [/v:<label>] [/q] [/a:<unitsize>] [/c] [/x] [/p:<passes>]
format <volume> [/v:<label>] [/q] [/f:<size>] [/p:<passes>]
format <volume> [/v:<label>] [/q] [/t:<tracks> /n:<sectors>] [/p:<passes>]
format <volume> [/v:<label>] [/q] [/p:<passes>]
format <volume> [/q]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `<volume>` | 指定要格式化的驱动器的装入点、卷名或驱动器号 (后面跟一个冒号) 。 如果未指定任何以下命令行选项，则**format**将使用卷类型来确定磁盘的默认格式。 |
| /fs： {FAT | FAT32 | NTFS | 指定文件系统的类型 (FAT、FAT32、NTFS) 。 |
| /v:`<label>` | 指定卷标。 如果省略了 **/v**命令行选项或在未指定卷标的情况下使用它，则格式化完成后，**格式**会提示你输入卷标。 使用语法 **/v:** 以防提示输入卷标。 如果使用单个 **format** 命令格式化多个磁盘，则会为所有磁盘指定相同的卷标。 |
| /a`<unitsize>` | 指定要在 FAT、FAT32 或 NTFS 卷上使用的分配单元大小。 如果未指定*unitsize*，则会根据卷大小进行选择。 对于常规使用，强烈建议采用默认设置。 以下列表显示了 NTFS、FAT 和 FAT32 *unitsize*的有效值：<ul><li>512</li><li>1024</li><li>2048</li><li>4096</li><li>8192</li><li>16K</li><li>32K</li><li>64K</li></ul>对于大小超过 512 字节的扇区，FAT 和 FAT32 还支持 128k 和 256k。 |
| /q | 执行快速格式化。 删除以前格式化的卷的文件表和根目录，但不会对错误区域执行逐个扇区扫描。 你应使用 **/q**命令行选项来仅设置你知道的状态良好的以前格式化的卷的格式。 请注意，**/q** 可替代 **/p**。 |
| /f`<size>` | 指定要格式化的软盘的大小。 如果可能，请使用此命令行选项，而不是 **/t**和 **/n**命令行选项。 Windows 可接受的大小值如下：<ul><li>1440或1440k 或1440kb</li><li>1.44、1.44 m 或 1.44 mb</li><li>1.44-MB，双面，四密度，3.5-英寸磁盘</li></ul> |
| /t:`<tracks>` | 指定磁盘上的磁道数。 如果可能，请改用 **/f**命令行选项。 如果使用 **/t** 选项，则还必须使用 **/n** 选项。 这些选项共同提供了指定正在格式化的磁盘大小的另一种方法。 此选项对 **/f** 选项无效。 |
| /n`<sectors>` | 指定每个磁道的扇区数。如果可能，请使用 **/f**命令行选项，而不是 **/n**。 如果使用 **/n**，则还必须使用 **/t**。 这两个选项共同提供了指定正在格式化的磁盘大小的另一种方法。 此选项对 **/f** 选项无效。 |
| /p`<passes>` | 归零卷上的每个扇区的指定操作数量。 此选项对 **/q** 选项无效。 |
| /c | 仅限 NTFS。 默认情况下，将压缩在新卷上创建的文件。 |
| /x | 在格式化之前，如有必要，会卸除卷。 针对卷的任何打开句柄将不再有效。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- **Format**命令为磁盘创建新的根目录和文件系统。 它还可以检查磁盘上的坏区，并可以删除磁盘上的所有数据。 若要使用新磁盘，必须先使用此命令格式化磁盘。

- 格式化软盘后，**格式**将显示以下消息：

    `Volume label (11 characters, ENTER for none)?`

    若要添加卷标签，请键入最多11个字符， (包括空格) 。 如果你不想将卷标添加到磁盘，请按 ENTER。

- 当使用**format**命令格式化硬盘时，会显示一条类似于下面的警告消息：

  ```
  WARNING, ALL DATA ON NON-REMOVABLE DISK
  DRIVE x: WILL BE LOST!
  Proceed with Format (Y/N)? _
  ```

  若要格式化硬盘，请按**Y**;如果不想格式化磁盘，请按**N**。

- FAT 文件系统将群集数量限制为不超过65526。 FAT32 文件系统将分类数限制为介于65527和4177917之间。

- 大小超过 4096 的分配单元不支持 NTFS 压缩。

  > [!NOTE]
  > 如果使用指定的群集大小确定以前的要求无法满足，则**Format**会立即停止处理。

- 格式化完成后，**格式**将显示显示总磁盘空间、标记为有缺陷的空格和文件可用空间的消息。

- 您可以使用 **/q**命令行选项加速格式设置过程。 仅在硬盘上没有损坏扇区的情况下使用此选项。

- 不应在使用**subst**命令准备的驱动器上使用**format**命令。 不能通过网络对磁盘进行格式化。

- 下表列出了每个退出代码以及其含义的简要说明。

  | 退出代码 | 说明 |
  | --------- | ----------- |
  | 0 | 格式化操作已成功。 |
  | 1 | 提供了不正确的参数。 |
  | 4 | 出现错误， (是0、1或 5) 以外的任何错误。 |
  | 5 | 用户按下了 N，以响应 "继续 (Y/N) 的格式？" 以停止此进程。 |

  可以结合使用 ERRORLEVEL 环境变量和 **if** 批处理命令来检查这些退出代码。

### <a name="examples"></a>示例

若要使用默认大小格式化驱动器 A 中的新软盘，请键入：

```
format a:
```

若要在驱动器 A 的以前格式化的软盘上执行快速格式化操作，请键入：

```
format a: /q
```

若要格式化驱动器 A 中的软盘，并为其分配卷标*数据*，请键入：

```
format a: /v:DATA
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc771080(v=ws.11))
