---
title: bootcfg raw
description: 适用于 bootcfg raw 的 Windows 命令主题，它将操作系统加载选项（指定为字符串）添加到 Boot.ini 文件的操作系统部分中的操作系统项。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e3458749-b0a0-460f-a022-3ff199a71f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fd5137187c5ba1dc1b410d728f1c2930ddcbc3cc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848510"
---
# <a name="bootcfg-raw"></a>bootcfg raw

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将指定为字符串的操作系统加载选项添加到 Boot.ini 文件的 **[操作系统]** 部分中的操作系统项。

## <a name="syntax"></a>语法
```
bootcfg /raw [/s <computer> [/u <Domain>\<User> /p <Password>]] <OSLoadOptionsString> [/id <OSEntryLineNum>] [/a]
```
### <a name="parameters"></a>参数

|         术语          |                                                                                                            Definition                                                                                                             |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     /s <computer>     |                                                        指定远程计算机的名称或 IP 地址（不使用反斜杠）。 默认值为本地计算机。                                                         |
| /u <Domain> \\<User>  |               使用 <User> 或 <Domain>\\<User>指定的用户的帐户权限运行命令。 默认为发出命令的计算机上当前登录用户的权限。                |
|     /p <Password>     |                                                                       指定在 **/u**参数中指定的用户帐户的密码。                                                                       |
| <OSLoadOptionsString> | 指定要添加到操作系统项的操作系统加载选项。 这些加载选项将替换与操作系统条目关联的任何现有加载选项。 未完成 <OSLoadOptions> 验证。 |
| /id <OSEntryLineNum>  |                       指定要更新的 Boot.ini 文件的 [操作系统] 部分中的操作系统条目行号。 [操作系统] 部分标题后面的第一行是1。                       |
|          /a           |                                                       指定要添加的操作系统选项应追加到任何现有的操作系统选项。                                                        |
|          /?           |                                                                                               在命令提示符下显示帮助。                                                                                                |

##### <a name="remarks"></a>备注
- **bootcfg raw**用于向操作系统项的末尾添加文本，并覆盖任何现有的操作系统输入选项。 此文本应包含有效的 OS 加载选项，例如 **/debug**、 **/fastdetect**、 **/nodebug**、 **/baudrate**、 **/crashdebug**和 **/sos**。 例如，以下命令将 **/debug/fastdetect**添加到第一个操作系统项的末尾，同时替换任何以前的操作系统项选项：
  ```
  bootcfg /raw /debug /fastdetect /id 1
  ```
  ## <a name="examples"></a><a name=BKMK_examples></a>示例
  下面的示例演示如何使用**bootcfg/raw**命令：
  ```
  bootcfg /raw /debug /sos /id 2
  bootcfg /raw /s srvmain /u maindom\hiropln /p p@ssW23 /crashdebug  /id 2
  ```
  ## <a name="additional-references"></a>其他参考
  - [命令行语法项](command-line-syntax-key.md)
