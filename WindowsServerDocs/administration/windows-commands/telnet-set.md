---
title: telnet set
description: 用于设置选项的 telnet 集的参考文章。
ms.topic: reference
ms.assetid: 67316b5f-9c6f-43e3-86d5-dcff9ae2ac3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 90b25b24da8af743d6e027bd26c2de7f155544b6
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038345"
---
# <a name="telnet-set"></a>telnet：设置

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

设置选项。

## <a name="syntax"></a>语法
```
set [bsasdel] [crlf] [delasbs] [escape <Char>] [localecho] [logfile <FileName>] [logging] [mode {console | stream}] [ntlm] [term {ansi | vt100 | vt52 | vtnt}] [?]
```
#### <a name="parameters"></a>参数

|                    参数                     |                                                                                                                                              说明                                                                                                                                              |
|--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                     bsasdel                      |                                                                                                                                 发送 **Backspace** 作为 **删除**。                                                                                                                                  |
|                       crlf                       |                                                                                                        按下 **Enter** 键时，发送 CR & LF (0x0D，0x 0A) 。 称为 "新行模式"。                                                                                                        |
|                     delasbs                      |                                                                                                                                 以**Backspace**形式发送**删除**。                                                                                                                                  |
|                esc <Character>                | 设置用于输入 telnet 客户端提示符的转义符。 转义符可以是单个字符，也可以是 **CTRL** 键加字符的组合。 若要设置控件键组合，请在键入要分配的字符时按住 **CTRL** 键。 |
|                    localecho                     |                                                                                                                                         启用本地回显。                                                                                                                                          |
|                日志 <FileName>                |                                                                                               将当前的 telnet 会话记录到本地文件。 设置此选项时，自动开始记录。                                                                                               |
|                     日志记录                      |                                                                                                                  启用日志记录。 如果未设置日志文件，将显示一条错误消息。                                                                                                                   |
|           模式 {控制台 &#124; 屏幕}           |                                                                                                                                       设置操作模式。                                                                                                                                        |
|                       ntlm                       |                                                                                                                                     启用 NTLM 身份验证。                                                                                                                                     |
| 术语 {ansi &#124; vt100 &#124; vt52 &#124; vtnt} |                                                                                                                                        设置终端类型。                                                                                                                                        |
|                        ?                         |                                                                                                                                    显示此命令的帮助。                                                                                                                                    |

## <a name="remarks"></a>注解
1. 您可以使用 "取消 **设置** " 命令关闭先前设置的选项。
2. 在非英语版本的 telnet 上， **codeset** <option> 可用。 **Codeset** <option> 将当前的代码集设置为一个选项，该选项可以是以下任意一项： **SHIFT JIS**、 **日语 EUC**、 **Jis 日本汉字**、 **jis 汉字 (78) **、 **DEC**日本汉字、 **NEC**日本汉字。 应在远程计算机上设置相同的代码集。
   ## <a name="examples"></a>示例
   设置日志文件并开始记录到本地文件 tnlog.txt
   ```
   set logfile tnlog.txt
   ```
   ## <a name="additional-references"></a>其他参考
3. - [命令行语法项](command-line-syntax-key.md)
