---
title: wbadmin get disks
description: 用于 wbadmin get 磁盘的 Windows 命令主题，其中列出了本地计算机当前联机的内部和外部磁盘。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 320edef1-df11-446b-a183-9f81811ef938
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0243edce77febddccc3497df34685113f2a1b48f
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80829760"
---
# <a name="wbadmin-get-disks"></a>wbadmin get disks



列出本地计算机当前处于联机状态的内部和外部磁盘。

若要列出使用此子命令联机的磁盘，您必须是**Backup Operators**组或**Administrators**组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行**wbadmin** 。 （若要打开提升的命令提示符，右键单击 "**命令提示符**"，然后单击 "以**管理员身份运行**"。）

## <a name="syntax"></a>语法

```
wbadmin get disks
```

### <a name="parameters"></a>参数

此子命令没有参数。

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBDisk](https://technet.microsoft.com/library/jj902446.aspx) cmdlet