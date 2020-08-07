---
title: 为服务器核心安装配置内存转储文件
description: 了解如何为 Windows Server 的 Server Core 安装配置内存转储文件
ms.mktglfcycl: manage
ms.sitesec: library
author: lizap
ms.localizationpriority: medium
ms.date: 10/17/2017
ms.openlocfilehash: ee5786684c4f3a6c75c3b123b9d3ef9d32143949
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87895885"
---
# <a name="configure-memory-dump-files-for-server-core-installation"></a>为服务器核心安装配置内存转储文件

>适用于： Windows Server 2019、Windows Server 2016 和 Windows Server (半年通道) 

使用以下步骤为服务器核心安装配置内存转储。

## <a name="step-1-disable-the-automatic-system-page-file-management"></a>步骤1：禁用自动系统页文件管理

第一步是手动配置系统故障和恢复选项。 这是完成剩余步骤所必需的。

运行下面的命令：

```
wmic computersystem set AutomaticManagedPagefile=False
```

## <a name="step-2-configure-the-destination-path-for-a-memory-dump"></a>步骤2：为内存转储配置目标路径

不需要在安装操作系统的分区上安装页面文件。 若要将页面文件放在另一个分区上，必须创建名为**DedicatedDumpFile**的新注册表项。 您可以使用**DumpFileSize**注册表项定义页面文件的大小。 若要创建 DedicatedDumpFile 和 DumpFileSize 注册表项，请执行以下步骤：

1. 在命令提示符处，运行**regedit**命令以打开注册表编辑器。
2. 找到并单击以下注册表子项： HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Control\CrashControl
3. 单击 "**编辑" > "新 > 字符串值**"。
4. 将新值命名为**DedicatedDumpFile**，然后按 enter。
5. 右键单击 " **DedicatedDumpFile**"，然后单击 "**修改**"。
6. 在 "**值数据**类型** \<Drive\> ： \\ \<Dedicateddumpfile.sys\> **" 中，然后单击 **"确定"**。

   >[!NOTE]
   > 将替换为 \<Drive\> 具有足够的磁盘空间用于分页文件的驱动器，并将替换为 \<Dedicateddumpfile.dmp\> 专用文件的完整路径。

7. 单击 "**编辑 > 新的 > DWORD 值**"。
8. 键入**DumpFileSize**，然后按 enter。
9. 右键单击 " **DumpFileSize**"，然后单击 "**修改**"。
10. 在 "**编辑 DWORD 值**" 的 "**基本**" 下，单击 "**十进制**"。
11. 在 "**值数据**" 中，键入适当的值，然后单击 **"确定"**。
    >[!NOTE]
    > 转储文件的大小为 mb (MB) 。
12. 退出注册表编辑器。

确定内存转储的分区位置之后，请配置页面文件的目标路径。 若要查看页面文件的当前目标路径，请运行以下命令：

```
wmic RECOVEROS get DebugFilePath
```

**DebugFilePath**的默认目标为%systemroot%\memory.dmp。 若要更改当前目标路径，请运行以下命令：

```
wmic RECOVEROS set DebugFilePath = <FilePath>
```

设置 \<FilePath\> 为目标路径。 例如，以下命令将内存转储目标路径设置为 C:\WINDOWS\MEMORY。DMP

```
wmic RECOVEROS set DebugFilePath = C:\WINDOWS\MEMORY.DMP
```

## <a name="step-3-set-the-type-of-memory-dump"></a>步骤3：设置内存转储类型

确定要为服务器配置的内存转储类型。 若要查看当前的内存转储类型，请运行以下命令：

```
wmic RECOVEROS get DebugInfoType
```

若要更改当前内存转储类型，请运行以下命令：

```
wmic RECOVEROS set DebugInfoType = <Value>
```

\<Value\>可以为0、1、2或3，如下所示。

- 0：禁用内存转储的删除。
- 1：完全内存转储。 当计算机意外停止时，记录系统内存的所有内容。 完整内存转储可能包含收集内存转储时正在运行的进程的数据。
- 2：内核内存转储 (默认) 。 仅记录内核内存。 这会在计算机意外停止时加快将信息记录到日志文件中的过程。
- 3：小内存转储。 记录可帮助识别计算机意外停止原因的最小有用信息集。

## <a name="step-4-configure-the-server-to-restart-automatically-after-generating-a-memory-dump"></a>步骤4：将服务器配置为在生成内存转储后自动重新启动

默认情况下，在生成内存转储后，服务器将自动重新启动。 若要查看当前配置，请运行以下命令：

```
wmic RECOVEROS get AutoReboot
```

如果**AutoReboot**的值为 TRUE，则在生成内存转储后，服务器将自动重新启动。 不需要任何配置，你可以继续下一步。

如果**AutoReboot**的值为 FALSE，则服务器不会自动重新启动。 运行以下命令以更改值：

```
wmic RECOVEROS set AutoReboot = true
```

## <a name="step-5-configure-the-server-to-overwrite-the-existing-memory-dump-file"></a>步骤5：将服务器配置为覆盖现有的内存转储文件

默认情况下，当创建新文件时，服务器将覆盖现有的内存转储文件。 若要确定现有内存转储文件是否已配置为要覆盖，请运行以下命令：

```
wmic RECOVEROS get OverwriteExistingDebugFile
```

如果值为1，则服务器将覆盖现有的内存转储文件。 不需要配置，你可以继续下一步。

如果该值为0，则服务器不会覆盖现有的内存转储文件。 运行以下命令以更改值：

```
wmic RECOVEROS set OverwriteExistingDebugFile = 1
```

## <a name="step-6-set-an-administrative-alert"></a>步骤6：设置管理警报

确定是否适合管理警报，并相应地设置**SendAdminAlert** 。 若要查看 SendAdminAlert 的当前值，请运行以下命令：

```
wmic RECOVEROS get SendAdminAlert
```

SendAdminAlert 的可能值为 TRUE 或 FALSE。 若要修改现有 SendAdminAlert 值为 true，请运行以下命令：

```
wmic RECOVEROS set SendAdminAlert = true
```

## <a name="step-7-set-the-memory-dumps-page-file-size"></a>步骤7：设置内存转储的页面文件大小

若要检查当前页面文件设置，请运行以下命令之一：

   ```
   wmic.exe pagefile
   ```

   or

   ```
   wmic.exe pagefile list /format:list
   ```

例如，运行以下命令来配置页面文件的初始大小和最大大小：

```
wmic pagefileset where name="c:\\pagefile.sys" set InitialSize=1000,MaximumSize=5000
```

## <a name="step-8-configure-the-server-to-generate-a-manual-memory-dump"></a>步骤8：配置服务器以生成手动内存转储

可以使用 PS/2 键盘手动生成内存转储。 默认情况下，此功能处于禁用状态，并且不能用于通用串行总线 (USB) 键盘。

若要使用 PS/2 键盘启用手动内存转储，请运行以下命令：

```
reg add HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\i8042prt\Parameters /v CrashOnCtrlScroll /t REG_DWORD /d 1 /f
```

若要确定是否已正确启用此功能，请运行以下命令：

```
Reg query HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ i8042prt \ Parameters / v CrashOnCtrlScroll
```

您必须重新启动服务器才能使更改生效。 可以通过运行以下命令来重新启动服务器：

```
Shutdown / r / t 0
```

你可以使用连接到服务器的 PS/2 键盘来生成手动内存转储，方法是在按下右 CTRL 键的同时按住滚动锁定键两次。 这会使计算机 bug 检查并出现错误代码0xE2。 重新启动服务器后，会在步骤2中创建的目标路径中显示一个新的转储文件。

## <a name="step-9-verify-that-memory-dump-files-are-being-created-correctly"></a>步骤9：验证是否正确创建了内存转储文件

你可以使用 dumpchk.exe utlity 来验证是否正确创建了内存转储文件。 dumpchk.exe 实用程序未随 Server Core 安装选项一起安装，因此你必须从具有桌面体验的服务器或从 Windows 10 中运行它。 此外，必须安装适用于 Windows 的调试工具。

利用 dumpchk.exe 实用程序，你可以使用所选的介质将内存转储文件从 Windows Server 2008 的服务器核心安装传输到其他计算机。

> [!WARNING]
> 页面文件可能非常大，因此请仔细考虑传输方法和该方法所需的资源。


其他参考

有关使用内存转储文件的常规信息，请参阅[Windows 的内存转储文件选项概述](https://support.microsoft.com/help/254649/overview-of-memory-dump-file-options-for-windows)。

有关专用转储文件的详细信息，请参阅[如何使用 DedicatedDeumpFile 注册表值克服系统驱动器上的空间限制，同时捕获系统内存转储](https://blogs.msdn.microsoft.com/ntdebugging/2010/04/02/how-to-use-the-dedicateddumpfile-registry-value-to-overcome-space-limitations-on-the-system-drive-when-capturing-a-system-memory-dump/)。



