---
title: logman 更新计数器
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 607df6d5-876c-428d-a0b3-f59cb244e2ce britw
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d93ea91fb1b5d105923457aeb8d5515e1ac5b9c5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80840570"
---
# <a name="logman-update-counter"></a>logman 更新计数器

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

更新现有计数器数据收集器的属性。  

## <a name="syntax"></a>语法  
```  
logman update counter <[-n] <name>> [options]  
```  
### <a name="parameters"></a>参数  

|                    参数                     |                                                                               说明                                                                               |
|--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                        /?                        |                                                                    显示区分上下文的帮助。                                                                     |
|                -s <computer name>                |                                                          在指定的远程计算机上执行命令。                                                          |
|                 -config <value>                  |                                                         指定包含命令选项的设置文件。                                                         |
|                   [-n] <name>                    |                                                                       目标对象的名称。                                                                        |
| -f < bin&#124;bincirc&#124;csv&#124;tsv&#124;sql > |                                                            指定数据收集器的日志格式。                                                             |
|             -[-] u < user [password] >              | 指定要以其身份运行的用户。 输入密码 \* 会生成密码提示。 在密码提示符下键入密码时，不会显示密码。 |
|    -m < [start] [stop] [[start] [stop] [...]]>    |                                                更改为手动启动或停止，而不是计划的开始或结束时间。                                                 |
|                -rf < [[hh：] mm：] ss >                |                                                        在指定的时间段内运行数据收集器。                                                         |
|        -b < M/d/yyyy h:mm： ss [AM&#124;PM] >         |                                                              开始在指定时间收集数据。                                                               |
|        -e < M/d/yyyy h:mm： ss [AM&#124;PM] >         |                                                               在指定的时间结束数据收集。                                                                |
|                -si < [[hh：] mm：] ss >                |                                                 指定性能计数器数据收集器的采样间隔。                                                  |
|              -o < 路径&#124;dsn！日志 >              |                                              指定 SQL 数据库中的输出日志文件或 DSN 和日志集名称。                                               |
|                      -[-] r                       |                                                  每日在指定的开始和结束时间重复数据收集器。                                                  |
|                      -[-] a                       |                                                                     追加到现有日志文件。                                                                     |
|                      -[-] o                      |                                                                     覆盖现有的日志文件。                                                                     |
|           -[-] v < nnnnnn&#124;mmddhhmm >           |                                                   将文件版本信息附加到日志文件名称的末尾。                                                   |
|                  -[-] rc <task>                   |                                                         运行每次关闭日志时指定的命令。                                                          |
|                 -[-] 最大值 <value>                  |                                                 最大日志文件大小（MB）或 SQL 日志的最大记录数。                                                  |
|              -[-] .cnf < [[hh：] mm：] ss >              |     指定 time 后，在指定的时间已过后创建新的文件。 如果未指定时间，则在超出最大大小时创建新文件。     |
|                        -y                        |                                                             在不提示的情况下回答 "是"。                                                              |
|                  -cf <filename>                  |                       指定列出要收集的性能计数器的文件。 该文件应包含每行一个性能计数器名称。                        |
|               -c < 路径 [path []] >               |                                                              指定要收集的性能计数器。                                                               |
|                   -sc <value>                    |                                      指定要使用性能计数器数据收集器收集的样本的最大数目。                                      |

## <a name="remarks"></a>备注  
其中列出了 [-]，额外-会对选项求反。  
## <a name="examples"></a><a name=BKMK_examples></a>示例  
以下命令将更新数据收集器 perf_log，将采样间隔更改为 "CSV"，并将日志格式更改为 "CSV"，并将版本控制添加到 "mmddhhmm" 格式的日志文件名。  
```  
logman update perf_log -si 10 -f csv -v mmddhhmm  
```  
## <a name="additional-references"></a>其他参考  
[logman](logman.md)  
[logman create 计数器](logman-create-counter.md)  
