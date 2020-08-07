---
title: bootcfg raw
description: Bootcfg raw 命令的参考文章，它将指定为字符串的操作系统加载选项添加到 Boot.ini 文件的操作系统部分中的操作系统项。
ms.topic: article
ms.assetid: e3458749-b0a0-460f-a022-3ff199a71f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9cba66ccebeacd21d337e04c97d935bd2c260b24
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880549"
---
# <a name="bootcfg-raw"></a>bootcfg raw

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将指定为字符串的操作系统加载选项添加到 Boot.ini 文件的 [操作系统] 部分中的操作系统项。 此命令将覆盖任何现有的操作系统输入选项。

## <a name="syntax"></a>语法

```
bootcfg /raw [/s <computer> [/u <domain>\<user> /p <password>]] <osloadoptionsstring> [/id <osentrylinenum>] [/a]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| `/s <computer>` | 指定远程计算机的名称或 IP 地址， (不要使用反斜杠) 。 默认为本地计算机。 |
| `/u <domain>\<user>`  | 使用或指定的用户的帐户权限运行命令 `<user>` `<domain>\<user>` 。 默认为发出命令的计算机上当前登录用户的权限。 |
| `/p <password>` | 指定在 **/u**参数中指定的用户帐户的密码。 |
| `<osloadoptionsstring>` | 指定要添加到操作系统项的操作系统加载选项。 这些加载选项将替换与操作系统条目关联的任何现有加载选项。 对于参数不进行验证 `<osloadoptions>` 。
| `/id <osentrylinenum>` | 在将操作系统加载选项添加到的 Boot.ini 文件的 "[操作系统]" 部分中指定操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。 |
| /a | 指定哪些操作系统选项应追加到任何现有的操作系统选项。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

此文本应包含有效的 OS 加载选项，例如 **/debug**、 **/fastdetect**、 **/nodebug**、 **/baudrate**、 **/crashdebug**和 **/sos**。

若要将 **/debug/fastdetect**添加到第一个操作系统条目的末尾，请替换以前的操作系统条目选项：

```
bootcfg /raw /debug /fastdetect /id 1
```

使用**bootcfg/raw**命令：

```
bootcfg /raw /debug /sos /id 2
bootcfg /raw /s srvmain /u maindom\hiropln /p p@ssW23 /crashdebug  /id 2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bootcfg 命令](bootcfg.md)
