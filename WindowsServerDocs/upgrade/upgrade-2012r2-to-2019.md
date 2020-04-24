---
title: 将 Windows Server 2012 R2 升级到 Windows Server 2019 | Microsoft Docs
description: 了解如何从 Windows Server 2012 R2 就地升级到 Windows Server 2019。
ms.prod: windows-server
ms.technology: server-general
ms.topic: upgrade
author: RobHindman
ms.author: robhind
ms.date: 09/16/2019
ms.openlocfilehash: 02d6dd21b798346245f209174902b6f4fdf24ff8
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "80853340"
---
# <a name="upgrade-windows-server-2012-r2-to-windows-server-2019"></a>将 Windows Server 2012 R2 升级到 Windows Server 2019

如果要保留相同的硬件和已设置的所有服务器角色而不平展服务器，则需要执行就地升级。 借助就地升级，可从较低版本的操作系统升级到较高版本的操作系统，同时使设置、服务器角色和数据保持不变。 本文可帮助你从 Windows Server 2012 R2 升级到 Windows Server 2019。

## <a name="before-you-begin-your-in-place-upgrade"></a>开始就地升级之前的准备工作

在开始 Windows Server 升级之前，建议从设备收集一些信息，以便进行诊断和故障排除。 由于此信息仅供升级失败时使用，必须确保将信息存储在可从设备访问的位置。

### <a name="to-collect-your-info"></a>收集信息

1. 打开命令提示符，转到 `c:\Windows\system32`，然后键入 systeminfo.exe  。

2. 复制、粘贴生成的系统信息，并将其存储在设备之外的某个位置。

3. 在命令提示符下键入 ipconfig/all，然后将生成的配置信息复制并粘贴到上述位置  。

4. 打开“注册表编辑器”，转到 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion hive，然后将 Windows Server BuildLabEx (version) 和 EditionID (edition) 复制并粘贴到上述位置   。

收集与 Windows Server 相关的所有信息后，我们强烈建议你备份操作系统、应用和虚拟机。 而且，还必须关闭、快速迁移或实时迁移当前正在服务器上运行的所有虚拟机    。 在就地升级期间，无法运行任何虚拟机。

## <a name="to-perform-the-upgrade"></a>执行升级

1. 请确保 BuildLabEx 值表明你正在运行 Windows Server 2012 R2  。

2. 找到 Windows Server 2019 安装程序介质，然后选择“setup.exe”  。

    ![显示 setup.exe 文件的 Windows 资源管理器](media/upgrade-2012r2-2019/setup-2019.png)

3. 选择“是”以启动安装过程  。

    ![用户帐户控制请求权限以启动安装](media/upgrade-2012r2-2019/start-setup-uac-box.png)

4. 对于连接到 Internet 的设备，请选择“下载更新、驱动程序和可选功能 (推荐)”选项，然后选择“下一步”   。

    ![选择联机以获取重要 Windows 更新的屏幕](media/upgrade-2012r2-2019/online-updates-win-setup.png)

5. 安装程序将检查设备配置，必须等待检查完成后再选择“下一步”  。

6. 根据从中收到 Windows Server 介质的分发渠道（零售、批量许可、OEM、ODM 等）和服务器的许可证，系统可能会提示输入授权密钥以继续操作。

7. 选择要安装的 Windows Server 2019 版本，然后选择“下一步”  。

    ![选择要安装的 Windows Server 2012 R2 版本的屏幕](media/upgrade-2012r2-2019/select-os-edition.png)

8. 根据分发渠道（例如零售、批量许可、OEM、ODM 等），选择“接受”即表示接受许可协议条款  。

    ![接受许可协议的屏幕](media/upgrade-2012r2-2019/license-terms.png)

9. 安装程序将建议你使用“添加/删除程序”删除 Microsoft Endpoint Protection  。

    此功能与 Windows Server 2019 不兼容。

10. 选择“保留个人文件和应用”以选择执行就地升级，然后选择“下一步”   。

    ![选择安装类型的屏幕](media/upgrade-2012r2-2019/choose-install-upgrade.png)

11. 安装程序在分析设备后，将提示你选择“安装”以继续进行升级  。

    ![显示你已准备好开始升级的屏幕](media/upgrade-2012r2-2019/ready-to-install.png)

    就地升级开始后，会在“升级 Windows”屏幕中显示进度  。 升级完成后，服务器将重启。

    ![显示升级进度的屏幕](media/upgrade-2012r2-2019/upgrading-windows-with-progress.png)

## <a name="after-your-upgrade-is-done"></a>升级完成后的步骤

升级完成后，必须确保已成功升级到 Windows Server 2019。

### <a name="to-make-sure-your-upgrade-was-successful"></a>确保已成功升级

1. 打开“注册表编辑器”，转到 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion hive 并查看 ProductName  。 此时应显示自己的 Windows Server 2019 版本，例如 Windows Server 2019 Datacenter  。

2. 请确保所有应用程序都处于运行状态，并且客户端成功连接到这些应用程序。

如果在升级期间出现问题，请复制和压缩 `%SystemRoot%\Panther`（通常为 `C:\Windows\Panther`）目录，并联系 Microsoft 支持部门。

## <a name="related-articles"></a>相关文章

- 有关 Windows Server 2019 的详细信息，请参阅 [Windows Server 2019 入门](https://docs.microsoft.com/windows-server/get-started-19/get-started-19)。