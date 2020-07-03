---
title: bootcfg rmsw
description: Bootcfg rmsw 命令的参考文章，用于删除指定操作系统项的操作系统加载选项。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fd7e4248-880e-4e2b-929e-87f8d44b9a63
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c905712b898501f45cbfc036d771f18232e82d5b
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924973"
---
# <a name="bootcfg-rmsw"></a>bootcfg rmsw

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

删除指定操作系统项的操作系统加载选项。

## <a name="syntax"></a>语法

```
bootcfg /rmsw [/s <computer> [/u <domain>\<user> /p <password>]] [/mm] [/bv] [/so] [/ng] /id <osentrylinenum>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址（请勿使用反斜杠）。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| /mm | 从指定的中删除/maxmem 选项及其关联的最大内存值 `<osentrylinenum>` 。 /Maxmem 选项指定操作系统可使用的最大 RAM 量。 |
| /bv | 从指定的中删除/basevideo 选项 `<osentrylinenum>` 。 /Basevideo 选项指示操作系统使用已安装视频驱动程序的标准 VGA 模式。 |
| /so | 从指定的中删除/sos 选项 `<osentrylinenum>` 。 /Sos 选项指示操作系统在加载时显示设备驱动程序名称。 |
| /ng | 从指定的中删除/noguiboot 选项 `<osentrylinenum>` 。 /Noguiboot 选项禁用出现在 CTRL + ALT + DEL logon 提示符之前的进度栏。 |
| `/id <osentrylinenum>` | 在将操作系统加载选项添加到的 Boot.ini 文件的 "[操作系统]" 部分中指定操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

使用**bootcfg/rmsw**命令：

```
bootcfg /rmsw /mm 64 /id 2
bootcfg /rmsw /so /id 3
bootcfg /rmsw /so /ng /s srvmain /u hiropln /id 2
bootcfg /rmsw /ng /id 2
bootcfg /rmsw /mm 96 /ng /s srvmain /u maindom\hiropln /p p@ssW23 /id 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
