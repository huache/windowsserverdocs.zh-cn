---
title: 生成多语言客户端还原介质
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 2fdbc016-d464-43cb-bd75-8a63e61588a2
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 8440fe0a32128182b86d26190c9b0448c64807d8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623917"
---
# <a name="build-multi-language-client-restore-media"></a>生成多语言客户端还原介质

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

> [!NOTE]
>  必须首先创建多语言 Windows 映像，如在将 Windows Server Essentials 述 pack 添加到 install 之前 [演练：多语言 Windows 映像创建](/previous-versions/windows/it-pro/windows-8.1-and-8/jj126995(v=win.10)) 中所述。

 生成多语言服务器安装 DVD 时，会为服务器 install.wim 安装语言包。 还原向导的本地化资源会作为语言包的一部分进行安装。

### <a name="to-build-a-multi-language-client-restore-media"></a>生成多语言客户端还原介质

1.  在 c:\mount 处装载 install.wim，我们将 c:\mount\Program Files\Windows Server\bin\ClientRestore 文件夹称为客户端还原介质的根文件夹：下面的 [RestoreMediaRoot]：

    ```
    dism /mount-wim /wimfile:install.wim /index:1 /mountdir:c:\mount
    ```

2.  在 [RestoreMediaRoot]\Sources\Boot.wim 处装载客户端还原 WIM 文件（还需要对 boot_x86.wim 执行相同步骤）。 命令行为：

    ```
    dism /mount-wim /wimfile:boot.wim /index:1 /mountdir:c:\mountRestore
    ```

3.  通过运行以下内容将 WinPE-Setup.cab 软件包添加到还原介质：

    ```
    dism /image:c:\mountRestore /add-package /packagepath:WinPE-Setup.cab
    ```

4.  使用记事本编辑 c:\mountRestore\windows\system32\winpeshl.ini，使用以下内容填充：

    ```
    [LaunchApp]
    AppPath = %SYSTEMDRIVE%\sources\SelectLanguage.exe
    ```

5.  将语言包添加到还原介质。 可以通过运行以下命令来添加语言包：

    ```
    dism /image:c:\mountRestore /add-package /packagepath:[language pack path]
    ```

     需要添加以下语言包：

    1.  WinPE 语言包 (lp.cab)

    2.  WinPE-Setup 语言包 (WinPE-Setup_[lang].cab，例如 WinPE-Setup_en-us.cab）

    3.  对于亚洲字体，包括 zh-cn、zh-tw、zh-hk、ko-kr 和 ja-jp，需要安装附加字体库（winpe-fontsupport-[语言].cab，例如 winpe-fontsupport-zh-cn.cab)

6.  通过运行以下内容生成新 Lang.ini 文件：

    ```
    dism /image:c:\mountRestore /Gen-LangINI /distribution:mount
    ```

7.  通过运行以下内容确认并卸载映像：

    ```
    dism /unmount-wim /mountdir:c:\mountRestore /commit
    ```

8.  对 [RestoreMediaroot]\Sources\Boot_x86.wim 重复步骤 2 到步骤 7。

9. 通过运行以下内容确认并卸载映像：

    ```
    dism /unmount-wim /mountdir:c:\mount /commit
    ```

## <a name="see-also"></a>另请参阅

 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)