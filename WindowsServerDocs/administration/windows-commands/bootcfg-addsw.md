---
title: bootcfg addsw
description: Bootcfg addsw 命令的参考文章，它为指定的操作系统条目添加操作系统加载选项。
ms.topic: article
ms.assetid: d8389293-ecd9-42f0-b84b-b9ead4cf52e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 549bfec84cb45baec309d8ae7043be39f5d31a3a
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880743"
---
# <a name="bootcfg-addsw"></a>bootcfg addsw

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

为指定的操作系统项添加操作系统加载选项。

## <a name="syntax"></a>语法

```
bootcfg /addsw [/s <computer> [/u <domain>\<user> /p <password>]] [/mm <maximumram>] [/bv] [/so] [/ng] /id <osentrylinenum>
```

### <a name="parameters"></a>参数

| 术语 | 定义 |
| ---- | ---------- |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| `/mm <maximumram>` | 指定操作系统可以使用的最大 RAM 量（以 mb 为单位）。 该值必须等于或大于 32 Mb。 |
| /bv | 将 **/basevideo**选项添加到指定的 `<osentrylinenum>` ，指导操作系统为安装的视频驱动程序使用标准 VGA 模式。 |
| /so | 将 **/sos**选项添加到指定的 `<osentrylinenum>` 中，指示操作系统在加载时显示设备驱动程序名称。 |
| /ng | 将 **/noguiboot**选项添加到指定的 `<osentrylinenum>` 中，禁用出现在 CTRL + ALT + DEL logon 提示符之前的进度栏。 |
| `/id <osentrylinenum>` | 在将操作系统加载选项添加到的 Boot.ini 文件的 "[操作系统]" 部分中指定操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用**bootcfg/addsw**命令：

```
bootcfg /addsw /mm 64 /id 2
bootcfg /addsw /so /id 3
bootcfg /addsw /so /ng /s srvmain /u hiropln /id 2
bootcfg /addsw /ng /id 2
bootcfg /addsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
