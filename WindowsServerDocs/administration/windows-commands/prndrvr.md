---
title: prndrvr
description: 用于添加、删除和列出打印机驱动程序的 prndrvr 命令的参考文章。
ms.topic: reference
ms.assetid: 82b09e3e-bd38-4df1-9953-b0e9ee2565a3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6fd276adb02281ab488c31db75563552f8495008
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638357"
---
# <a name="prndrvr"></a>prndrvr

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

添加、删除和列出打印机驱动程序。 此命令是位于目录中的 Visual Basic 脚本 `%WINdir%\System32\printing_Admin_Scripts\<language>` 。 若要在命令提示符下使用此命令，请键入 **cscript** ，然后键入 prndrvr 文件的完整路径，或将目录更改为相应的文件夹。 例如：`cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prndrvr`。

使用不带参数的 **prndrvr** 将显示命令行帮助。

## <a name="syntax"></a>语法

```
cscript prndrvr {-a | -d | -l | -x | -?} [-m <model>] [-v {0|1|2|3}] [-e <environment>] [-s <Servername>] [-u <Username>] [-w <password>] [-h <path>] [-i <inf file>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| -a | 安装驱动程序。 |
| -d | 删除驱动程序。 |
| -l | 列出由 **-s** 参数指定的服务器上安装的所有打印机驱动程序。 如果未指定服务器，Windows 会列出安装在本地计算机上的打印机驱动程序。 |
| -X | 删除由 **-s** 参数指定的服务器上的逻辑打印机未使用的所有打印机驱动程序和其他打印机驱动程序。 如果未指定要从列表中删除的服务器，Windows 将删除本地计算机上所有未使用的打印机驱动程序。 |
| -m `<model_name>` | 按名称指定要安装的驱动程序)  (。 驱动程序通常是以支持的打印机型号命名的。 有关详细信息，请参阅打印机文档。 |
| `-v {0|1|2|3}` | 指定要安装的驱动程序的版本。 有关适用于哪个环境的版本的信息，请参阅 **-e**参数的描述。 如果未指定版本，则会安装适用于在其上安装驱动程序的计算机上运行的 Windows 版本的驱动程序版本。 |
| -e `<environment>` | 指定要安装的驱动程序的环境。 如果未指定环境，则使用要安装驱动程序的计算机的环境。 支持的环境参数包括： **WINDOWS NT x86**、 **Windows X64** 或 **windows IA64**。 |
| -s `<Servername>` | 指定承载要管理的打印机的远程计算机的名称。 如果未指定计算机，则使用本地计算机。 |
| -u `<Username>` -w `<password>` | 指定有权连接到承载要管理的打印机的计算机的帐户。 目标计算机的本地管理员组的所有成员都具有这些权限，但也可以向其他用户授予权限。 如果未指定帐户，则必须使用具有这些权限的帐户登录，才能使命令正常工作。 |
| -h `<path>` | 指定驱动程序文件的路径。 如果未指定路径，则将使用安装 Windows 的位置的路径。 |
| -i `<filename.inf>` | 指定要安装的驱动程序的完整路径和文件名。 如果未指定文件名，该脚本将使用 Windows 目录的 inf 子目录中的某个收件箱打印机 .inf 文件。<p>如果未指定驱动程序路径，则脚本将在 driver.cab 文件中搜索驱动程序文件。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果提供的信息包含空格，请使用引号将文本括起来 (例如，"Computer Name" ) 。

- **-X**参数删除在运行) Windows 的备用版本的客户端上使用的所有附加打印机驱动程序 (驱动程序，即使正在使用主驱动程序也是如此。 如果安装了传真组件，此选项也会删除传真驱动程序。 如果主传真驱动程序未使用，则将其删除 (也就是说，如果不存在使用它) 的队列。 如果删除了主传真驱动程序，则重新启用传真的唯一方法是重新安装传真组件。

### <a name="examples"></a>示例

若要列出本地 printServer1 服务器上的所有驱动程序 \\ ，请键入：

```
cscript prndrvr -l -s
```

若要为激光打印机型号1型号的打印机添加版本 3 Windows x64 打印机驱动程序，请使用 c:\temp\Laserprinter1.inf 驱动程序信息文件存储在 c：\temp 文件夹中的驱动程序的驱动程序信息文件，键入：

```
cscript prndrvr -a -m Laser printer model 1 -v 3 -e Windows x64 -i c:\temp\Laserprinter1.inf -h c:\temp
```

若要删除适用于激光打印机型号1的版本 3 Windows x64 打印机驱动程序，请键入：

```
cscript prndrvr -a -m Laser printer model 1 -v 3 -e Windows x64
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)
