---
title: pnpunattend
description: 用于对计算机上的设备驱动程序进行审核并执行无提示驱动程序安装的 pnpunattend 命令的参考文章。
ms.topic: article
ms.assetid: 4fa88932-cff0-4dfc-936c-98c0e3dfbeb8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 72cb158804bcec3c57ef9bae8d21f8e15a7978d9
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884931"
---
# <a name="pnpunattend"></a>pnpunattend

审核计算机上的设备驱动程序，执行无人参与的驱动程序安装，或者在不安装的情况下搜索驱动程序，还可以在命令行中报告结果。 使用此命令为特定硬件设备指定特定驱动程序的安装。

## <a name="prerequisites"></a>先决条件

旧版本的 Windows 操作系统需要进行初步准备。 在使用此命令之前，必须完成以下任务：

1. 为要安装的驱动程序创建一个目录。 例如，在**C:\Drivers\Video**中为视频适配器驱动程序创建一个文件夹。

2. 下载并提取设备的驱动程序包。 将包含操作系统版本 INF 文件的子文件夹的内容复制到所创建的视频文件夹中的所有子文件夹。 例如，将视频驱动程序文件复制到**C:\Drivers\Video**。

3. 将系统环境路径变量添加到步骤1中创建的文件夹。例如， **C:\Drivers\Video**。

4. 创建以下注册表项，然后为创建的**DriverPaths**键将**值数据**设置为**1**。

5. 对于 Windows®7导航注册表路径： **HKEY_LOCAL_Machine \Software\microsoft\windows NT\CurrentVersion \\ **，然后创建密钥： **UnattendSettings\PnPUnattend\DriverPaths \\ **

## <a name="syntax"></a>语法

```
PnPUnattend.exe auditsystem [/help] [/?] [/h] [/s] [/l]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|--|--|
| auditsystem | 指定联机驱动程序安装。<p>必需，但在运行此命令时，无论是 **/help**还是 **/？** 个参数。 |
| /s | 可选。 指定在不安装的情况下搜索驱动程序。 |
| /l | 可选。 指定在命令提示符中显示此命令的日志信息。 |
| `/? | /help` | 可选。 在命令提示符下显示此命令的帮助。 |

### <a name="examples"></a>示例

若要命令显示如何使用**PNPUnattend.exe**审核计算机的可能的驱动程序更新，然后将发现结果报告给命令提示符，请键入：

```
pnpunattend auditsystem /s /l
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
