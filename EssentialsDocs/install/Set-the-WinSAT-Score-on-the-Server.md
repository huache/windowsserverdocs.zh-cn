---
title: 在服务器上设置 WinSAT 分数
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 911dc494-0f8f-4723-93d6-2106f914b906
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 56769966cbfb6778c06abc4ba07d21f258e900a4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623344"
---
# <a name="set-the-winsat-score-on-the-server"></a>在服务器上设置 WinSAT 分数

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

应为运行 Windows Server Essentials 操作系统的服务器设置 WinSAT CPU 分数，以优化视频流分辨率。 此操作可通过创建和安装包含 WinSAT 分数信息的 .xml 文件来完成。

## <a name="obtain-the-winsat-cpu-score"></a>获取 WinSAT CPU 分数
 OPK 中提供了一个名为 WinServerSAT.exe 的程序，该程序用于发现 WinSAT CPU 分数并将该信息放入 WinServerSAT.xml 文件中供操作系统读取。

#### <a name="to-obtain-the-winsat-cpu-score"></a>获取 WinSAT CPU 分数

1. 将 \\ ADK 媒体中的 Resources\WinServerSAT * 复制到引用计算机。

2. 在引用计算机中，打开提升的命令提示符窗口。

3. 如果 %ProgramFiles%\Windows Server\Bin\OEM 文件夹不存在，则输入以下命令，然后按 Enter 键。

    **mkdir "%ProgramFiles%\Windows Server\Bin\OEM"**

4. 输入以下命令，然后按 Enter 键。

    **WinServerSAT.exe "%ProgramFiles%\Windows Server\Bin\OEM\WinServerSAT.xml"**

   以下示例显示了创建的 WinServerSAT.xml 文件的 XML 内容。

```

<?xml version="1.0" encoding="UTF-16"?>
<WinSAT>
   <CpuScore description="WinSAT CPU score">WinSAT_Score</CpuScore>
</WinSAT>
```

 其中，*WinSAT_Score* 将替换为在服务器上发现的值。

> [!IMPORTANT]
>  捕获映像之前，必须从引用计算机中删除 WinServerSAT.exe、winsat.prx、winsat.wmv 和 WinSATEncode.wmv 文件。
